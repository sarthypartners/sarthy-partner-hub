# Update Protocol

Read this before editing anything in `content/`. It applies equally whether you're a human on the terminal or an AI assistant (Claude Code or otherwise) making the change.

## The rule

1. Before editing a file in `content/`, open `meta/dependency-map.md` and find that document in the left column.
2. Every document listed in the right column must be reviewed for impact **in the same working session** — not deferred, not left for someone to notice later.
3. If a right-column document actually needs a change, make it now. If it doesn't, that's fine — but the review has to happen, not just the edit.
4. Bump the `version` field for any document you changed, and update its `updated` field to a short plain-English note (not just a date) in `content/manifest.json`.
5. Add one line to `content/changelog.json` describing the structural change — new sections, renamed tabs, status changes. Content edits within an existing section don't need a changelog line; structural changes do.
6. If your change introduces a dependency not already listed in `meta/dependency-map.md`, add it there in the same commit.
7. Run `python3 build.py` before committing, so `dist/index.html` always reflects the current `content/` state. Never hand-edit `dist/index.html` directly — it's generated, and direct edits will be overwritten on the next build.
8. Commit with a message that names what changed and what else you checked, e.g. `git commit -m "Update Gap & Risk Register; checked Partnership SOP v1.0 Section 13, no change needed"`.

## Why this exists instead of a fully automatic system

There is no code that detects when a downstream document actually needs new content — that requires judgment. What CAN be automated (and is, via Cloudflare Pages watching this repo) is *republishing*: once you push, the hosted hub rebuilds and goes live without anyone manually redeploying. The judgment step — deciding what downstream content should say — stays a deliberate step in this protocol, not a background process. Treat step 1–3 above as non-negotiable, even when it feels obvious that nothing downstream needs to change.

## What to actually hand over, if you're not pushing directly

If you're preparing files for someone else to apply (rather than pushing yourself): ship `content/` every time. Also ship `build.py` if you touched it, and `meta/` if you touched it — never assume the person already has your latest version of either. State explicitly which folders are in the handoff and which weren't touched. This has been gotten wrong before (a real round shipped `content/` only, when `build.py` had also changed) — say it plainly rather than assume it's obvious.

## For an AI assistant picking up this repo cold

If you're an AI assistant asked to make an update here and you weren't part of earlier sessions: read `meta/dependency-map.md`, `meta/style-guide.md`, and `content/manifest.json` in full before touching anything. Don't assume a document is self-contained — the whole point of this structure is that most of them aren't. Example commit message: `git commit -m "Update Gap & Risk Register; checked Data Dictionary and Segmentation Framework, no change needed"`.
