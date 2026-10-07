---
name: quantum-extraction
description: "Extracts page-by-page content, equations, diagrams, and terminology from quantum computing slides and assignment documents."
---

# Purpose

To extract complete technical notes, equations, circuit representations, and slide text from PDF slide decks and assignment materials without losing substantive detail.

# When to Use

Use when initiating the processing of new quantum computing slide decks, lecture PDFs, or assignment documents.

# Procedure

1. **Input Gate:**
   - Recover current task, settled criteria, original PDF source/path, source versions, current gate, and repair history.
   - Verify readability of the input PDF. For missing context or unreadable files, mark gate as `MANUAL`/`BLOCKED` and state missing files.
2. **Work:**
   - Inventory every slide page sequentially.
   - Extract raw text, key terms, equations, circuit descriptions, and diagram descriptions.
   - Map each extracted point to its specific slide page number.
3. **Change:**
   - Separate reusable scope from run criteria. Mark affected content `STALE` if source files update and resume extraction for changed pages.
4. **Correction:**
   - Report findings and corrections for independent recheck against the original source slides.
   - Increment repair count `0→1→2` only after delivery of a complete corrected extraction. If correction 2 fails, retain `BLOCKED` and halt automation for manual transfer.
5. **Handoff:**
   - Report a compact context checkpoint containing page-by-page coverage, unresolved visual content, and extraction completeness (`READY`/`PASS`/`REVISE`/`BLOCKED`).
6. **Stop/Resume:**
   - Stop upon complete slide extraction or capability block. Resume dependent gate upon validated inputs.

# Quality Checks

- Ensure 100% page coverage with explicit mapping to slide numbers.
- Preserve all quantum mathematical notation and circuit descriptions.
- Flag any unreadable visual elements explicitly as uncertain.

# Failure Cases

- If PDF text is unreadable or corrupted, set status to `BLOCKED` and request readable input/images.
- If repair count reaches 2 without passing recheck, stop automation for manual handoff.

# Output Expectations

Returns page-mapped structured research notes containing raw text, slide concepts, equations, and flagged visual elements.