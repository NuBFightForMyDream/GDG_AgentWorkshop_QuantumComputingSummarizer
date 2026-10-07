---
name: quantum-slide-processor
description: "Entry coordination skill that manages slide extraction, prose writing, visual diagramming, and independent review for quantum computing materials."
---

# Purpose

Coordinates the end-to-end execution of processing quantum computing PDF slide decks and assignments into readable summaries, visual workflow diagrams, and independently verified study materials.

# When to Use

Use when starting a job to turn quantum computing PDF slides or assignments into readable documentation, basic summaries, and visual workflows. Triggered when run inputs (e.g., slide PDF path) are provided or need to be requested.

# Procedure

1. **Input Gate:**
   - Recover current task, settled criteria, readable source files (PDF slide paths or attachments), artifact versions, gate, repair history, and target output directory (defaults to `<project-root>/outputs/`).
   - If PDF sources are missing or unreadable, request readable PDF attachments, verified file paths, or slide images.
2. **Work:**
   - Sequential Delegation:
     a. Delegate source extraction to `quantum-slide-extractor`.
     b. Pass extraction notes to `quantum-content-writer` for prose drafting and coverage mapping.
     c. Pass draft to `quantum-visualizer` to insert Mermaid diagrams and circuit visualizers.
     d. Pass completed draft, original source slides, and criteria to `quantum-reviewer` for independent review.
   - Coordinator Verification: Confirm reviewer inspected original source slides directly and verified 100% page coverage.
   - File Saving: Save approved final document to `<project-root>/outputs/quantum_summary_and_workflows.md`.
   - Read-Back Verification: Reopen saved deliverable file and verify content matches approved draft.
3. **Change:**
   - Separate reusable scope from run criteria. Mark affected deliverables `STALE` if source files or criteria change and restart earliest affected worker gate.
4. **Correction:**
   - Report findings and route corrections back to responsible worker (`quantum-slide-extractor`, `quantum-content-writer`, or `quantum-visualizer`).
   - Increment repair count `0→1→2` only after delivery of complete corrected deliverable. If correction 2 fails independent recheck, retain `BLOCKED`, halt automation, and present manual handoff.
5. **Handoff:**
   - Present compact context checkpoint, absolute path of verified saved deliverable, summary of quantum basics, generated workflows, embedded diagram list, and human decision boundary.
6. **Stop/Resume:**
   - Stop after coordinator acceptance of reviewed deliverable or capability block. Resume dependent gate on validated input or authorized change.

# Quality Checks

- Verify sequential execution: Extraction -> Writing -> Visualization -> Independent Review -> Coordinator Acceptance.
- Ensure saved deliverable path is verified via read-back before final human handoff.
- Confirm independent reviewer inspected original PDF sources directly.

# Failure Cases

- If PDF input is unreadable or missing, request readable PDF files or manual extract transfer.
- If file writing or read-back verification fails, mark persistence `BLOCKED` while retaining approved content.
- If repair count reaches 2 without passing independent recheck, stop automation and provide manual handoff.

# Output Expectations

Saves verified deliverable to `<project-root>/outputs/quantum_summary_and_workflows.md` and provides summary of basic concepts, workflow guide, embedded diagram specs, and verified file paths.