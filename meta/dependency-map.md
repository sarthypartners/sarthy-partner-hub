# Dependency Map

This is the authoritative source for "if you change X, check Y." Both the human team and any AI assistant working in this repo (via terminal or chat) should consult this file before considering an update finished. If `build.py` ever renders a dependency table inside the hub itself, it should be generated FROM this file, not maintained separately — this file is the single source of truth for dependencies, not a copy of it.

**Note on Partnership SOP section numbers below:** the SOP has been restructured and renumbered multiple times (absorbing Sarthy's original Playbook 2.0, merging four planned SOP documents into itself, adding the deal-closure and dormancy sections). Section numbers referenced here match the SOP as of v6.1 (23 sections). If the SOP gets renumbered again, this table needs a pass to match — that itself is a dependency, see the last row.

| If this changes... | ...check and update these |
|---|---|
| Phase 0 Discussion Doc (once Sarthy answers) | Partnership SOP #5-10 (fees, wallet, lead flow, credit rules, disputes, withdrawal), #19 (KPI framework), #20 (referral fee) |
| Current-State Assessment | Gap & Risk Register, Partner Segmentation Framework, Partner Journey Map |
| Gap & Risk Register | Partnership SOP's problem-related sections, Master Execution Sequence priority order, Action Item & Blocker Tracker (critical findings now live in both — keep them in sync, not duplicated) |
| Data Dictionary | Interim Operating System (uses these exact field definitions), Partner Segmentation Framework (the `giving_pattern` field is defined jointly across both) |
| Partner Segmentation Framework | Partnership SOP #11 (Giver/Taker/Balanced — summarize, don't copy in full), #17 (Winning back inactive partners), Migration Wave Plan (once drafted), Interim Operating System (call queue logic) |
| Partner Journey Map | Partnership SOP #14 (summarize, don't copy in full), Communication Template Library |
| Communication Template Library | Partnership SOP #16 (the link, not the content), #17 (Reactivation) |
| Any section of Partnership SOP — any change, not just when it becomes confirmed | Business Requirements Document — it cites specific SOP sections directly; check it didn't just go stale |
| Business Requirements Document | Low-Level System Specification (once drafted), Action Item & Blocker Tracker (integration requirement items reference BRD section numbers) |
| Alpha to Beta Graduation Criteria | Migration Wave Plan, Partnership SOP #18 |
| Interim Operating System | Action Item & Blocker Tracker (the data migration section links here) |
| Action Item & Blocker Tracker | Gap & Risk Register, Business Requirements Document, Project Plan (Gantt View) - all three reference or link to it |
| Project Plan (Gantt View) | Roadmap (phase definitions must stay consistent), Action Item & Blocker Tracker |
| Glossary | Whichever document actually changed the definition - Partnership SOP, Data Dictionary, or Segmentation Framework are the most common sources; the Glossary should never be the source of truth for a term's meaning, only a pointer to it |
| Master Execution Sequence (reordered) | This file - if the reorder changes which document feeds which |
| Partnership SOP §2 (origin story) or §10 (withdrawal/cycle rules) | Design History & Decisions - both sections point here for the full story. If the current-design facts in either section change again, check the History page hasn't gone stale by comparison |
| Master Execution Sequence's item 11, or its note on unnumbered documents | Design History & Decisions - both explanations live there now |
| Design History & Decisions, if edited | Partnership SOP §2 and §10, and Master Execution Sequence - confirm their pointer links still make sense given what History now says |
| Migration Wave Plan | Graduation Criteria (Wave 2 gate), Segmentation Framework (wave-candidate criteria), Action Item & Blocker Tracker (readiness gates) |
| Alpha to Beta Graduation Criteria, if the target changes | Migration Wave Plan's Wave 2 gate references this document's criteria directly |

| Business Requirements Document, any MVP/Phase 2 tag or requirement change | Low-Level System Specification and Replit Build Brief - both were built directly from the BRD's current state |
| Low-Level System Specification (state machines, formulas, operations) | Replit Build Brief - references it directly rather than duplicating; keep both in sync |
| Partnership SOP §19 (KPI measures), if changed | Reporting Dashboard and BRD §13 - both cite the measures directly, not their own copy |

## When you add a new document

Add a row here before (or in the same commit as) adding the document itself. An undocumented dependency is worse than an obvious one - it fails silently. This instruction exists specifically because it wasn't followed consistently for several rounds in a row - worth treating as a real commit-blocking checklist item, not a suggestion.
