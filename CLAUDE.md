# Strategic Partners Playbook 3.0 - Sarthy Project Hub

This is a hosted documentation hub for a Sarthy Strategic Partners consulting engagement. It's built as a single-page HTML app, assembled by `build.py` from structured content files, rather than hand-written directly.

## Before doing anything else

Read these three files in full - they are not optional background reading, they are the actual operating rules for this repo:

1. `meta/update-protocol.md` - the exact steps required before any edit counts as "done"
2. `meta/dependency-map.md` - which document depends on which; check this before treating any change as complete
3. `meta/style-guide.md` - the writing rules; each one exists because something specific went wrong without it

## What this repo is

- `content/` - every document's actual content, plus `manifest.json` (drafted docs), `queued.json` (not yet written - currently empty, all 24 originally planned documents are drafted), `categories.json`, `changelog.json`
- `meta/` - the three files above, plus `custom-domain.txt`
- `build.py` - reads everything in `content/` and generates `dist/index.html`, the actual hub. **Never hand-edit `dist/index.html` directly** - it's overwritten on every build.
- Hosting is **Cloudflare Pages**, connected directly to this GitHub repo - it watches for pushes to `main` and rebuilds automatically. There is no GitHub Actions workflow involved; an earlier one existed and was deliberately removed when the project switched away from GitHub Pages.

## Standing rules

- Every document has a `status` of `draft` or `done` in `manifest.json` - reflect this honestly, don't mark something `done` just because text exists for it.
- Internal cross-references between documents use real links: `<a href="#" onclick="showDoc('doc-id');return false;" class="xlink">text</a>` - not plain text mentions of a document's name.
- Run `python3 build.py` after any content change, before considering the change complete.
- Bump the relevant document's `version` and `updated` fields in `manifest.json` when its content changes.
- Log structural changes (new documents, renamed sections, category changes) in `content/changelog.json` - not every small wording edit, but anything that changes the hub's shape.
- The Lead's working assumptions (unconfirmed by Sarthy) should read as such in the text itself - phrases like "working assumption, pending Sarthy sign-off" are load-bearing, not decoration. Don't quietly upgrade something to sounding confirmed.

## Style

See `meta/style-guide.md` for the full rules. In short: plain English, short but connected sentences, no first or second person outside literal message templates, and current-state content kept separate from historical rationale (which lives on the Design History & Decisions page).
