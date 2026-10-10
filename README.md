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

Nothing in this repo is tied to GitHub Pages. The move is three steps and needs no code change. (Vercel and HubSpot are both possible next homes; pick one.)

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

## Moving to HubSpot

HubSpot does not host a repo. The page becomes a HubSpot website page, so this move is a short rebuild, not a re-point. The files here are the source for it.

1. **Upload the assets.** Put the three images in the HubSpot file manager.
2. **Make the template.** In the design manager, create a coded template from `index.html` and a stylesheet from `styles.css`. Point the image and stylesheet paths at the uploaded files.
3. **Swap the contact links for a form.** Every call to action here is a `mailto:info@empwrhvac.com` link. Replace the main one (`#contact`) with a HubSpot form so submissions land in the CRM. The HubSpot tracking code is added by HubSpot on its own pages.
4. **Connect the domain.** In HubSpot, open Settings, then Content, then Domains & URLs. Connect `www.empwrhvac.com` as the primary website domain and set `empwrhvac.com` to redirect to it. HubSpot shows the exact DNS records.
5. **Switch DNS at GoDaddy.** Replace only the web records (`A` on `@`, `CNAME` on `www`) with the ones HubSpot shows. **Do not touch the MX or TXT records.**

Then turn off GitHub Pages as described above. Rollback is the same: put the GitHub Pages records back.
