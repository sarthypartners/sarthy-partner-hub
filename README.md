# Sarthy Strategic Partners — Project Hub

A hosted, single-URL reference for every document in this engagement. Content lives as separate files in `content/`; `build.py` assembles them into `dist/index.html`; a GitHub Action rebuilds and republishes automatically on every push to `main`.

## One-time setup (run once, by whoever owns this)

1. Create a free GitHub account if you don't have one: https://github.com/signup
2. Create a new **public** repository (Settings → repository visibility can stay public even if the content is sensitive, since GitHub Pages needs public repos on the free tier — if that's a concern, flag it and we'll look at a private-repo-compatible host instead).
3. On your machine, inside this folder, run:
   ```
   git init
   git add .
   git commit -m "Initial hub setup"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<your-repo-name>.git
   git push -u origin main
   ```
4. In the GitHub repo, go to **Settings → Pages**, and under "Build and deployment," set Source to **GitHub Actions**.
5. Push will trigger the workflow automatically. After a minute or two, your hub is live at `https://<your-username>.github.io/<your-repo-name>/`.

### Pointing projecthub.sarthy.com at it (custom domain)

This repo is already configured to publish under `projecthub.sarthy.com` — see `meta/custom-domain.txt`. Two more steps, one from you and one from whoever manages Sarthy's DNS:

**You, in the GitHub repo:**
- Go to **Settings → Pages**, and under "Custom domain," enter `projecthub.sarthy.com`, then save.
- Once DNS (below) is in place and has propagated, tick **Enforce HTTPS** in the same settings panel.

**Send this to Sarthy's IT/DNS admin — this is the entire ask, no server access needed:**
> Please add a DNS CNAME record:
> - Host/Name: `projecthub`
> - Type: `CNAME`
> - Value/Target: `<your-username>.github.io`
> - TTL: default (or 3600)
>
> This points `projecthub.sarthy.com` at a page we host separately — no changes needed to the existing sarthy.vip portal or its infrastructure.

DNS changes can take anywhere from a few minutes to a few hours to propagate. Once it resolves, `projecthub.sarthy.com` serves the hub directly, and every future `git push` republishes to that same address automatically — nothing further to coordinate with IT after this one-time record is added.

That's the only manual setup. Everything after this is steps 1–3 below, repeated.

## Ongoing update workflow (every time content changes)

1. Read `meta/update-protocol.md` and `meta/dependency-map.md` before editing anything.
2. Edit the relevant file(s) in `content/`. Update `content/manifest.json` (version, updated note) and `content/changelog.json` if the change is structural.
3. Run `python3 build.py` locally to confirm it builds without errors (optional but recommended — the Action will also catch failures).
4. Commit and push:
   ```
   git add .
   git commit -m "Describe what changed and what you checked in the dependency map"
   git push
   ```
5. The GitHub Action rebuilds `dist/index.html` and republishes automatically — no manual redeploy step. Check the "Actions" tab in GitHub if you want to confirm it succeeded.

## Folder structure

```
content/
  manifest.json       - metadata for every drafted document (status, version, title, etc.)
  queued.json          - documents not yet drafted, shown as placeholders in the hub
  categories.json       - category order and hover descriptions
  changelog.json        - structural change log shown in the hub's Version History tab
  <id>.html             - the actual content of each drafted document
meta/
  dependency-map.md     - which document feeds which; check this before any edit
  update-protocol.md    - the rule for how to make an update correctly
  custom-domain.txt     - the domain this hub publishes under; build.py writes it into dist/CNAME
build.py                 - generates dist/index.html from everything above
dist/
  index.html             - the built hub; never hand-edit this, it's regenerated
.github/workflows/
  deploy.yml              - the automation that republishes on every push
```
