# Dependency Map

This is the authoritative source for "if you change X, check Y." Both the human team and any AI assistant working in this repo (via terminal or chat) should consult this file before considering an update finished. If `build.py` ever renders a dependency table inside the hub itself, it should be generated FROM this file, not maintained separately — this file is the single source of truth for dependencies, not a copy of it.

| If this changes... | ...check and update these |
|---|---|
| Phase 0 Discussion Doc (once Sarthy answers) | Partnership SOP v1.0 §4 (Commercial Mechanics), §11 (Escalation SOP), §13 (KPI Framework) |
| Current-State Assessment | Gap & Risk Register, Partner Segmentation Framework, Partner Journey Map |
| Gap & Risk Register | Partnership SOP v1.0 Appendix D, Master Execution Sequence priority order |
| Data Dictionary / SSOT Schema | Interim Operating System, Partnership SOP v1.0 Appendix B |
| Partner Segmentation Framework | Partnership SOP v1.0 §6, Partner Journey Map, Dormant-Partner Reactivation Process, Migration Wave Plan |
| Partner Journey Map | Partnership SOP v1.0 §5, Communication Template Library, Onboarding Process |
| Communication Template Library | Partnership SOP v1.0 Appendix A, Dormant-Partner Reactivation Process |
| Onboarding Process / Engagement Cadence | Partnership SOP v1.0 §7 & §8 |
| Escalation & Dispute SOP | Partnership SOP v1.0 §11 |
| Partnership SOP v1.0 (any section moving to Confirmed) | Business Requirements Document — re-check no requirement still cites a Pending section |
| Business Requirements Document | Low-Level System Specification |
| Alpha → Beta Graduation Criteria | Migration Wave Plan |
| Master Execution Sequence (reordered) | This file — if the reorder changes which document feeds which |

## When you add a new document

Add a row here before (or in the same commit as) adding the document itself. An undocumented dependency is worse than an obvious one — it fails silently.
