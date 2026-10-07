---
name: quantum-review
description: "Independently reviews written summaries, visual diagrams, and workflows against original quantum computing slides and assignment criteria."
---

# Purpose

To conduct an independent audit comparing written documents, workflows, and visual diagrams directly against original quantum computing slides and assignment sources to verify fidelity, page coverage, and mathematical accuracy.

# When to Use

Use after content draft and visual diagrams are generated to perform independent verification prior to final coordinator acceptance.

# Procedure

1. **Input Gate:**
   - Recover current task, settled criteria, original PDF slides/assignments, draft document with diagrams, coverage table, source/artifact versions, current gate, and repair history.
   - Verify readability of original slides and generated draft. If original source or draft is uninspected or unreadable, mark gate as `MANUAL`/`BLOCKED` and request original attachments or verified paths.
2. **Work:**
   - Acknowledge exact pages and draft bytes inspected.
   - Perform page-by-page comparison between original slides and draft content.
   - Verify that all key concepts, equations, and assignment steps are preserved without omission or unauthorized modification.
   - Audit visual diagrams (Mermaid syntax, circuit logic, workflow sequences) against source slides.
   - Record page-by-page coverage, omissions, altered claims, unsupported additions, and unresolved visuals with explicit slide references.
3. **Change:**
   - Separate reusable scope from run criteria. Mark affected audit items `STALE` if source files or drafts update and re-audit changed sections.
4. **Correction:**
   - Report findings, owner, and specific corrections for recheck against original sources.
   - Increment repair count `0→1→2` only after a complete corrected draft/diagram set is delivered. If correction 2 fails recheck, retain `BLOCKED`, stop automation, and provide manual review handoff.
5. **Handoff:**
   - Report a compact context checkpoint with inspected page count, discrepancy list, diagram validity checks, and status (`READY`/`PASS`/`REVISE`/`BLOCKED`).
6. **Stop/Resume:**
   - Stop after completed independent review or missing capability. Resume dependent gate on usable input or authorized correction.

# Quality Checks

- Verify 100% page coverage against original slides and assignments.
- Confirm syntax and logical correctness of all embedded Mermaid diagrams.
- Ensure any additions beyond source slides are explicitly labeled in an enrichment section.

# Failure Cases

- If original slides cannot be directly inspected by the reviewer, mark gate as `BLOCKED` and request readable PDF files or slide page images.
- If repair count reaches 2 without passing recheck, stop automation for manual handoff.

# Output Expectations

Returns independent review audit report containing page-by-page coverage analysis, discrepancy log, diagram verification, and pass/fail determination.