# Savi hosting site

**Live at `https://moonie556.github.io/savi-app-site/`** — deployed 2026-08-25 to the public repo `https://github.com/moonie556/savi-app-site` via GitHub Pages, all four routes verified with a real HTTP 200 check. This directory is that repo's source; pushing to its `main` branch redeploys the site automatically.

Four static pages, no build step, no dependencies beyond Google Fonts (loaded via `<link>`, same as the rest of the app's docs):

- `index.html` — landing page (usable as the App Store Connect **Marketing URL**)
- `privacy-policy.html` — **Privacy Policy URL**
- `terms-of-service.html` — linked from Terms, not a required ASC field on its own
- `support.html` — **Support URL**

Content is copied faithfully from `../Privacy Policy.dc.html` and `../Terms of Service.dc.html` (the versions that went to legal review and came back approved 2026-08-20 — see `BACKLOG.md`), rewritten as plain self-contained HTML instead of the `doc-page.js` custom-element viewer those originals depend on, so they render reliably with no JS runtime for App Review and real users.

**One deliberate change from the originals**: the "Template notice" disclaimer box ("this is a starting draft, not legal advice, must be reviewed by counsel before publication") was removed from both legal pages. That was accurate when first drafted but is stale now — the legal review happened and came back approved, and Solace Labs LLC is filed. Publishing a live legal page that says "not yet reviewed" when it has been would be confusing at best. If a fuller review happens later, re-add a note here rather than reviving that box.

## Redeploying after an edit

This folder is a git repo (`origin` → `github.com/moonie556/savi-app-site`). Commit and push to `main`; GitHub Pages rebuilds automatically within a minute or two:

```
git add -A && git commit -m "update copy" && git push
```

## Live URLs

- `https://moonie556.github.io/savi-app-site/` → **Marketing URL**
- `https://moonie556.github.io/savi-app-site/privacy-policy.html` → **Privacy Policy URL**
- `https://moonie556.github.io/savi-app-site/support.html` → **Support URL**
- `https://moonie556.github.io/savi-app-site/terms-of-service.html` (linked from both legal pages, not its own required ASC field)

## Alternative hosts (not used, kept for reference)

Netlify/Vercel both have a "drag a folder in" deploy flow if this ever needs to move off GitHub Pages — drag `hosting/` onto app.netlify.com/drop or vercel.com/new.

## Local preview

```
npx serve hosting -l 4173
```
