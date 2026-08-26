# Savi hosting site

Four static pages, no build step, no dependencies beyond Google Fonts (loaded via `<link>`, same as the rest of the app's docs):

- `index.html` — landing page (usable as the App Store Connect **Marketing URL**)
- `privacy-policy.html` — **Privacy Policy URL**
- `terms-of-service.html` — linked from Terms, not a required ASC field on its own
- `support.html` — **Support URL**

Content is copied faithfully from `../Privacy Policy.dc.html` and `../Terms of Service.dc.html` (the versions that went to legal review and came back approved 2026-08-20 — see `BACKLOG.md`), rewritten as plain self-contained HTML instead of the `doc-page.js` custom-element viewer those originals depend on, so they render reliably with no JS runtime for App Review and real users.

**One deliberate change from the originals**: the "Template notice" disclaimer box ("this is a starting draft, not legal advice, must be reviewed by counsel before publication") was removed from both legal pages. That was accurate when first drafted but is stale now — the legal review happened and came back approved, and Solace Labs LLC is filed. Publishing a live legal page that says "not yet reviewed" when it has been would be confusing at best. If a fuller review happens later, re-add a note here rather than reviving that box.

## Deploy (recommended: GitHub Pages, free, ~5 minutes)

1. Push this `hosting/` folder's contents to a new GitHub repo (or a `docs/` folder / `gh-pages` branch of an existing one).
2. Repo → Settings → Pages → Source: deploy from that branch/folder.
3. GitHub gives you a URL like `https://<username>.github.io/<repo>/`. Use:
   - `.../index.html` (or just the root) → **Marketing URL**
   - `.../privacy-policy.html` → **Privacy Policy URL**
   - `.../support.html` → **Support URL**
4. Optional: a custom domain (e.g. `savi.app`) can be attached to GitHub Pages later — not required for App Store Connect, which accepts any real URL.

## Alternative: Netlify or Vercel drag-and-drop

Both have a "drag a folder in" deploy flow that needs no CLI or account setup beyond signing in — drag this `hosting/` folder onto app.netlify.com/drop or vercel.com/new, get a live URL immediately.

## Local preview

```
npx serve hosting -l 4173
```
