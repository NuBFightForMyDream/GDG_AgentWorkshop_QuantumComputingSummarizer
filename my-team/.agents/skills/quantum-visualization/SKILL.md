---
name: quantum-visualization
description: "Generates clear visual diagrams, quantum circuit layouts, state diagrams, and workflow charts from written quantum computing concepts."
---

# Purpose

To transform written quantum computing explanations and workflows into precise visual structures, including Mermaid flowcharts, state transitions, circuit representations, and process flow diagrams.

# When to Use

Use after draft explanations and workflows are written to generate embedded visual diagrams for slide summaries and assignment solutions.

# Procedure

1. **Input Gate:**
   - Recover current task, settled criteria, draft explanations, workflow descriptions, artifact versions, current gate, and repair history.
   - Verify readability of written workflows and descriptions. If draft inputs are missing or incomplete, mark gate as `MANUAL`/`BLOCKED` and request written draft input.
2. **Work:**
   - Translate quantum circuit steps, state transformations, and workflow protocols into Mermaid diagram code or ASCII circuit layouts.
   - Design flowcharts for algorithm execution steps (e.g., initialization, Hadamard transformation, oracle application, phase kickback, measurement).
   - Embed diagrams cleanly into the corresponding sections of the written draft document.
3. **Change:**
   - Separate reusable scope from run criteria. Mark affected visual components `STALE` if source text changes and regenerate modified diagrams.
4. **Correction:**
   - Report findings and corrections for independent recheck against the original draft and slide criteria.
   - Increment repair count `0→1→2` only after delivery of complete corrected visual diagrams. If correction 2 fails, retain `BLOCKED` and halt automation for manual handoff.
5. **Handoff:**
   - Report a compact context checkpoint containing diagram count, format checks, and visualization completeness (`READY`/`PASS`/`REVISE`/`BLOCKED`).
6. **Stop/Resume:**
   - Stop upon complete diagram integration or missing input. Resume dependent gate upon validated inputs.

# Quality Checks

- Ensure all Mermaid diagrams render syntactically valid code.
- Verify quantum circuit steps accurately map to gates and operations described in the source text.
- Ensure visual flowcharts logically represent execution sequences.

# Failure Cases

- If written workflows lack operational details needed for diagram generation, set status to `BLOCKED` and request workflow clarification.
- If repair count reaches 2 without passing recheck, stop automation for manual handoff.

# Output Expectations

Returns draft document enriched with syntactically valid Mermaid diagrams, state charts, and quantum circuit representations.