# Style Guide

The writing rules for everything in `content/`. These weren't designed up front - they were refined through real corrections across many editing rounds. Where a rule exists because something specific went wrong, that's noted, so the reasoning doesn't get lost.

## Sentence structure

- **Short sentences. One idea per sentence.** Most sentences should be under ~20 words.
- **But short isn't the actual goal - clear and connected is.** Splitting a sentence can go wrong: cutting the word "but" or "so" between two ideas can leave the second sentence meaningless on its own, even though it's grammatically simple. Before finalizing a split, check: does this sentence secretly depend on something the previous one implied but never actually said? If yes, keep one connecting word rather than two orphaned fragments.
- **No nested parentheticals.** Don't interrupt a sentence's main clause with a dash-bounded aside. Finish the thought, then start a new sentence for the aside.
- **Don't cram 3+ distinct facts into one sentence** using semicolons or multiple dashes. Each fact gets its own sentence, or its own line in a list/table.
- **Use "X, not Y" sparingly.** It's a real tool for a genuine contrast, not a default sentence pattern. Overused, it reads as a formula, not a person explaining something.

## Voice

- **No first person** ("I," "I'll," "we," "We") in reader-facing content. This isn't just a style preference - a document written as one person's promises to one specific reader breaks the moment anyone else (Sarthy, the Associate, a future team member) reads it. State the standing process instead: not "I'll check the table," but "the table gets checked."
- **No second person** ("you," "your") **except** inside a literal message template or call script meant to be spoken directly to a partner (Communication Template Library, Interview Guide's actual script lines). Those are correctly second-person - they're real messages to a real recipient. Don't extend that exception to narration *about* those documents.
- **Use role names, not pronouns**, when attributing responsibility: Lead, Associate, Sarthy, admin, partner. If a sentence needs "we" to make sense, it usually means a role name was left out.
- **Exception: FAQ-style questions** phrased as if a partner is asking ("Do I lose my credits if...?") are a normal, legitimate convention - different in kind from document narration. Leave these alone.

## Content structure - To-Be vs. As-Is

- **The main body of a document describes what's true right now.** History, rationale, and "what this used to be" content goes on the Design History & Decisions page instead - linked to, not narrated inline.
- **Exception: Current-State Assessment.** Its entire purpose is being a historical/evidence record - the To-Be extraction principle doesn't apply to it. It still follows every other rule in this guide (sentence structure, voice), just not this one.
- **Don't leave meta-commentary about the hub's own editing history in reader-facing content** - phrases like "this resolves the earlier contradiction between X and Y" or "unlike the previous version of this rule." A reader doesn't need to know about an internal bug that got fixed; they need the clean current rule. That history belongs in `content/changelog.json`, not in the document body.

## Accuracy discipline

- **Verify before asserting.** Grep or view the actual file before claiming something is true, missing, or fixed - especially before telling the user a check passed.
- **When fixing one instance of a bug, search the whole hub for the same pattern before considering it done.** The clearest example: an early voice-cleanup pass searched for "I"/"I'll" but never checked "we" - 27 more instances survived that pass entirely, found only because a later, separate check happened to catch one leftover case. Define the full pattern being searched for, not just the one example that was flagged.
- **When a fact or number appears in more than one document, changing it in one place means finding every other place it appears.** Real bugs have been caused by this - the same "dispute escalation is unresolved" claim survived, stale, in three separate documents after the actual resolution had been made.
- **After every content change:** rebuild (`python3 build.py`), and check every `showDoc()` reference still resolves to a real document ID (a short Python script using `manifest.json` as the source of truth - this has been run repeatedly throughout the project and should stay a standing habit, not a one-time check).

## Dependency and cross-reference discipline

- **Any new document gets a row in `meta/dependency-map.md` in the same round it's added** - not deferred. This has been missed multiple times and had to be caught and fixed after the fact.
- **`content/guide.html`'s hub-facing dependency table should mirror `meta/dependency-map.md`.** They're two separately-maintained copies of the same information right now - keep both in sync manually until (or unless) the hub is changed to generate one from the other.
- **When one document extracts content into another** (like the History page), add the reverse dependency too: if the destination document is edited, what needs checking back in the source.

## Shipping discipline

- **A zip is a complete, cumulative snapshot of `content/` at that moment - never a partial patch.** Say this explicitly every time: "this zip supersedes everything before it."
- **If `build.py` changed, ship it in the same zip as `content/`.** If `meta/` changed, ship that too. State plainly which folders are included and which weren't touched - don't make the person guess.
- **Before telling someone a zip contains a specific fix, verify it by unzipping and grepping the actual zip contents** - not just trusting that the working folder and the zip must match.

## Tone

High-school-grade, plain English. Minimal. Every sentence should earn its place - if it doesn't change what the reader needs to know or do, cut it.
