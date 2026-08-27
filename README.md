# Savi hosting site

**Live at `https://savipeersupport.org/`** — deployed 2026-08-25 to the public repo `https://github.com/Savi-Peer-Support/savi-app-site` via GitHub Pages, all four routes verified with a real HTTP 200 check. This directory is that repo's source; pushing to its `main` branch redeploys the site automatically.

**Custom domain added 2026-08-27**: the user registered `savipeersupport.org` and it's now the live custom domain on this Pages site (was `savi-peer-support.github.io/savi-app-site/` before). DNS is 4 A records (`185.199.108/109/110/111.153`) at the registrar, plus a `CNAME` file in this repo. HTTPS cert issuance got stuck for ~2 hours with `https_enforced: false` despite DNS being fully correct — fixed by removing and recreating the GitHub Pages site entirely (`DELETE`/`POST` on the `/pages` API, not just clearing the custom domain field — a `DELETE` on that endpoint removes the whole Pages configuration, worth remembering if this ever needs troubleshooting again), which picked the domain back up automatically from the committed `CNAME` file and issued a working cert on the fresh attempt.

Four static pages, no build step, no dependencies beyond Google Fonts (loaded via `<link>`, same as the rest of the app's docs):

- `index.html` — landing page (usable as the App Store Connect **Marketing URL**)
- `privacy-policy.html` — **Privacy Policy URL**
- `terms-of-service.html` — linked from Terms, not a required ASC field on its own
- `support.html` — **Support URL**

Content is copied faithfully from `../Privacy Policy.dc.html` and `../Terms of Service.dc.html` (the versions that went to legal review and came back approved 2026-08-20 — see `BACKLOG.md`), rewritten as plain self-contained HTML instead of the `doc-page.js` custom-element viewer those originals depend on, so they render reliably with no JS runtime for App Review and real users.

**One deliberate change from the originals**: the "Template notice" disclaimer box ("this is a starting draft, not legal advice, must be reviewed by counsel before publication") was removed from both legal pages. That was accurate when first drafted but is stale now — the legal review happened and came back approved, and Solace Labs LLC is filed. Publishing a live legal page that says "not yet reviewed" when it has been would be confusing at best. If a fuller review happens later, re-add a note here rather than reviving that box.

## Redeploying after an edit

This folder is a git repo (`origin` → `github.com/Savi-Peer-Support/savi-app-site`). Commit and push to `main`; GitHub Pages rebuilds automatically within a minute or two:

```
git add -A && git commit -m "update copy" && git push
```

## Live URLs

- `https://savipeersupport.org/` → **Marketing URL**
- `https://savipeersupport.org/privacy-policy.html` → **Privacy Policy URL**
- `https://savipeersupport.org/support.html` → **Support URL**
- `https://savipeersupport.org/terms-of-service.html` (linked from both legal pages, not its own required ASC field)

## Alternative hosts (not used, kept for reference)

Netlify/Vercel both have a "drag a folder in" deploy flow if this ever needs to move off GitHub Pages — drag `hosting/` onto app.netlify.com/drop or vercel.com/new.

## Local preview

```
npx serve hosting -l 4173
```
