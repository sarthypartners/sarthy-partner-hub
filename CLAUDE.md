# Strategic Partners Playbook 3.0 - Sarthy Project Hub

This is a hosted documentation hub for a Sarthy Strategic Partners consulting engagement. It's built as a single-page HTML app, assembled by `build.py` from structured content files, rather than hand-written directly.

## Before doing anything else

Read these two files in full - they are not optional background reading, they are the actual operating rules for this repo:

1. `meta/update-protocol.md` - the exact steps required before any edit counts as "done"
2. `meta/dependency-map.md` - which document depends on which; check this before treating any change as complete

## What this repo is

- `content/` - every document's actual content, plus `manifest.json` (drafted docs), `queued.json` (not yet written), `categories.json`, `changelog.json`
- `meta/` - the two files above, plus `custom-domain.txt`
- `build.py` - reads everything in `content/` and generates `dist/index.html`, the actual hub. **Never hand-edit `dist/index.html` directly** - it's overwritten on every build.
- `wrangler.jsonc` - Cloudflare Pages config; deploys `dist/` as static assets. This replaced the old GitHub Pages workflow.

## Standing rules

- Every document has a `status` of `pending`, `draft`, or `done` in `manifest.json` - reflect this honestly, don't mark something `done` just because text exists for it.
- Internal cross-references between documents use real links: `<a href="#" onclick="showDoc('doc-id');return false;" class="xlink">text</a>` - not plain text mentions of a document's name.
- Run `python3 build.py` after any content change, before considering the change complete.
- Bump the relevant document's `version` and `updated` fields in `manifest.json` when its content changes.
- Log structural changes (new documents, renamed sections, category changes) in `content/changelog.json` - not every small wording edit, but anything that changes the hub's shape.
- The Lead's working assumptions (unconfirmed by Sarthy) should read as such in the text itself - phrases like "working assumption, pending Sarthy sign-off" are load-bearing, not decoration. Don't quietly upgrade something to sounding confirmed.

## Style

Plain, everyday English throughout - this hub is written so a non-technical reader understands it without a second guess. Avoid jargon; where a technical term is unavoidable, explain it in the same sentence.
