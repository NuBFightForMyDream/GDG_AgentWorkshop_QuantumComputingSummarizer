---
name: quantum-writing
description: "Converts extracted quantum computing slide notes into structured readable prose, basic summaries, and step-by-step workflow guides."
---

# Purpose

To synthesize page-mapped quantum computing slide notes and assignment concepts into readable explanations, foundational summaries (qubits, gates, superposition, entanglement), and clear step-by-step workflows.

# When to Use

Use after raw slide extraction is complete to draft readable documentation, summary notes, and assignment solutions.

# Procedure

1. **Input Gate:**
   - Recover current task, settled criteria, page-mapped extraction notes, artifact versions, current gate, and repair history.
   - Verify readability of extraction notes. If notes are missing or unreadable, mark gate as `MANUAL`/`BLOCKED` and request extracted inputs.
2. **Work:**
   - Convert bullet points into clear narrative prose while preserving quantum concepts and exact technical terms.
   - Structure core summaries covering quantum basics (state vectors, Dirac notation, quantum gates, measurement, algorithms).
   - Format step-by-step workflows for quantum algorithms and assignment solving protocols.
   - Provide a page-to-draft coverage table mapping draft sections to source slide pages.
3. **Change:**
   - Separate reusable scope from run criteria. Mark affected sections `STALE` if source notes change and re-draft modified sections.
4. **Correction:**
   - Report findings and corrections for independent recheck against original extraction notes and criteria.
   - Increment repair count `0→1→2` only after delivery of a complete corrected draft. If correction 2 fails, retain `BLOCKED` and halt automation for manual handoff.
5. **Handoff:**
   - Report a compact context checkpoint containing draft status, coverage mapping, and completeness (`READY`/`PASS`/`REVISE`/`BLOCKED`).
6. **Stop/Resume:**
   - Stop upon completed draft delivery or missing input. Resume dependent gate upon validated inputs.

# Quality Checks

- Verify every substantive point from source slides is reflected in the prose.
- Ensure page-to-draft coverage table accounts for all extracted pages.
- Keep authorized enrichments strictly separated and labeled.

# Failure Cases

- If extraction notes lack necessary detail, set status to `BLOCKED` and request re-extraction.
- If repair count reaches 2 without passing recheck, stop automation for manual handoff.

# Output Expectations

Returns readable prose document containing quantum summaries, structured workflows, and a page-to-draft coverage table.