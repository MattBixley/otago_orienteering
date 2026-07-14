# How the `/admin` login works (OAuth)

This site's content admin at **`/admin/`** is [Sveltia CMS](https://github.com/sveltia/sveltia-cms).
Editors don't touch code — they log in with GitHub and edit events, results
and pages through web forms. Saving a form writes a commit to this repo, which
triggers the GitHub Pages build, and the change goes live in a minute or two.

This document explains the login (OAuth) piece: why it's needed, how to set it
up once, and how to add or remove editors.

---

## Why OAuth is needed at all

The CMS runs entirely in the editor's browser (it's a static site — there is no
application server). To save changes it calls the **GitHub API on the editor's
behalf**, so it needs a GitHub *access token* for that person.

GitHub hands out a token only after the user logs in and approves the app. That
approval step exchanges a temporary `code` for a token, and **that exchange
requires a client secret**. A secret can never live in browser JavaScript
(anyone could read it), so a tiny server-side helper has to do the exchange.

That helper is the only "backend" this site needs. It is small, free to run,
and does nothing except the GitHub login handshake.

```
Editor's browser                 Auth helper (Cloudflare Worker)      GitHub
─────────────────                ───────────────────────────────     ──────
1. Click "Login with GitHub" ─────────────────────────────────────►  GitHub login page
2. Approve the app  ◄──────────────────────────────────────────────  (user says yes)
3. GitHub redirects back with a temporary ?code=… ──►  Worker
                                                       exchanges code
                                                       + CLIENT_SECRET ──►  GitHub
                                                       ◄── access token ──
4. Worker hands the token back to the browser ◄──────
5. CMS uses the token to read/write the repo ─────────────────────►  GitHub API
```

The client secret lives only inside the Worker (step 3). The browser only ever
sees the final token for the logged-in user.

---

## The backend config

The CMS is told which backend and auth helper to use in
[`admin/config.yml`](admin/config.yml):

```yaml
backend:
  name: github
  repo: MattBixley/otago_orienteering   # org/repo the CMS commits to
  branch: main
  base_url: https://<your-auth-worker>.workers.dev   # the auth helper (see below)
```

- `name: github` — log in with a GitHub account (simplest for a small committee).
- `repo` / `branch` — where saved changes are committed.
- `base_url` — the auth helper's address. Sveltia calls `base_url/auth` to start
  login and `base_url/callback` to finish it. **Omit `base_url` and login will
  not work** — there is no default public helper.

> If `base_url` is missing, Sveltia falls back to the old Netlify OAuth service,
> which is deprecated. Always set your own `base_url`.

---

## One-time setup

Do this once. Two pieces: a GitHub OAuth App (issues the secret) and the auth
helper Worker (holds the secret).

### 1. Create a GitHub OAuth App

1. GitHub → your profile → **Settings → Developer settings → OAuth Apps → New OAuth App**.
   (For an org-owned repo, do this under the org's settings instead.)
2. Fill in:
   - **Application name:** `Otago Orienteering CMS`
   - **Homepage URL:** `https://mattbixley.github.io/otago_orienteering/`
   - **Authorization callback URL:** `https://<your-auth-worker>.workers.dev/callback`
     (you'll get the worker URL in step 2 — come back and paste it here)
3. Create it. Note the **Client ID**, and **Generate a new client secret** — copy
   it now, GitHub shows it once.

### 2. Deploy the auth helper (Cloudflare Worker — free)

The maintained helper is **[`sveltia/sveltia-cms-auth`](https://github.com/sveltia/sveltia-cms-auth)**.

Easiest path (no local tooling):
1. Sign in at [Cloudflare](https://dash.cloudflare.com/) (free account).
2. **Workers & Pages → Create → Import a repository** (or use the repo's
   "Deploy to Cloudflare" button in its README).
3. After it deploys, note the Worker URL, e.g.
   `https://sveltia-cms-auth.<your-name>.workers.dev`.
4. In the Worker's **Settings → Variables**, add:

   | Variable | Value |
   |----------|-------|
   | `GITHUB_CLIENT_ID` | Client ID from step 1 |
   | `GITHUB_CLIENT_SECRET` | Client secret from step 1 |
   | `ALLOWED_DOMAINS` | `mattbixley.github.io` (restricts who the helper will serve) |

5. Go back to the GitHub OAuth App and set the **callback URL** to
   `https://<that worker URL>/callback`.

### 3. Point the site at the helper

Set `base_url` in `admin/config.yml` to the Worker URL (no trailing slash) and
commit. Login is now live at `https://mattbixley.github.io/otago_orienteering/admin/`.

---

## Adding and removing editors

Login authenticates *who* someone is; **repo write access decides what they can
do.** To let someone edit:

1. Repo → **Settings → Collaborators → Add people** → their GitHub username →
   role **Write**.
2. They accept the invite, go to `/admin/`, click **Login with GitHub**, approve
   once, and can edit.

To remove an editor, remove them as a collaborator. For an org-owned repo, use a
team with Write access instead of individual collaborators — easier to manage.

There are **no separate CMS passwords** to hand out or rotate — GitHub accounts
are the identity, repo access is the permission.

---

## Optional: editors without GitHub accounts

If some volunteers won't have GitHub accounts, switch the backend to
`git-gateway` and invite editors by email via an identity service. This is more
setup and the common free option (Netlify Identity) is being wound down, so for
a small trusted committee the GitHub backend above is the simpler, more durable
choice. See the website-options review (`_reviews/website-options-review.md`)
for the trade-offs.

---

## Troubleshooting

| Symptom | Likely cause |
|---------|--------------|
| "Login" does nothing / popup closes instantly | `base_url` wrong or Worker not deployed |
| Redirect error / "redirect_uri mismatch" | Callback URL in the OAuth App ≠ `base_url/callback` |
| Logs in but "failed to persist" on save | Editor lacks **Write** access to the repo |
| Login works for you, not others | `ALLOWED_DOMAINS` too narrow, or they're not collaborators |
| Was working, now "Netlify" error | `base_url` got removed from `config.yml` |
