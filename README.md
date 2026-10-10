# EMPWR HVAC site

The one-page site for [empwrhvac.com](https://empwrhvac.com). Plain static files. No build step, no dependencies.

| File | What it is |
|---|---|
| `index.html` | The page |
| `styles.css` | All styling |
| `empwr-e.png`, `empwr-wordmark.png` | Logo |
| `home-comfort.webp` | Hero image |
| `CNAME`, `.nojekyll` | GitHub Pages settings. Other hosts ignore them. |

To change the page, edit `index.html` or `styles.css` and push to `main`. The host redeploys on push.

## Hosting today

GitHub Pages, served from the root of `main`. This is temporary.

## Moving to Vercel

Nothing in this repo is tied to GitHub Pages. The move is three steps and needs no code change.

1. **Import the repo.** In Vercel, choose Add New, then Project, then import this repo. Framework preset: **Other**. Leave the build command and output directory empty. Vercel serves the repo root as is.
   - If the Vercel team cannot see this GitHub org, transfer the repo to EMPWR's org first (Settings, then Transfer), or push a copy there.
2. **Add the domains.** In the Vercel project, open Settings, then Domains. Add `empwrhvac.com` and `www.empwrhvac.com`. Vercel shows the exact DNS records it wants.
3. **Switch DNS at GoDaddy.** Replace only the web records below with the ones Vercel shows. **Do not touch the MX or TXT records.** They carry email for `info@empwrhvac.com`.

| Record | GitHub Pages value (today) | Change to |
|---|---|---|
| `A` on `@` (four records) | `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153` | The `A` value Vercel shows |
| `CNAME` on `www` | `solarinbound.github.io` | The `CNAME` value Vercel shows |

After the domain shows as valid in Vercel:

- Turn off GitHub Pages in this repo (Settings, then Pages, then Unpublish).
- Delete `CNAME` and `.nojekyll`. They do nothing on Vercel.

Rollback: put the GitHub Pages records back. Pages keeps serving until it is turned off.
