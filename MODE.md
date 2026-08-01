# MODES.md

# Task

- Analyze — Understand the project.
- Debug — Find and explain problems.

---

# Analysis Depth

Choose the minimum depth that answers the user's question.

## Content

Understand what the mod provides.

Focus on:

- Features
- Gameplay
- XML
- Project structure
- Dependencies

Avoid implementation details.

---

## Architecture

Understand how the mod works.

Focus on:

- System architecture
- Runtime flow
- Harmony patches
- Module interaction
- XML ↔ Code interaction

Explain representative implementations instead of every class.

---

## Implementation

Understand how the implementation executes.

Focus on:

- Decompiled source
- Call chains
- Runtime behavior
- Critical algorithms
- Reflection
- Performance-critical logic

Investigate only details relevant to the current task.

---

# Depth Escalation

Start with the shallowest depth.

Increase the depth only when:

- current evidence is insufficient;
- runtime behavior cannot be explained;
- implementation details become necessary;
- the user requests deeper analysis.

Briefly explain why the depth changed.
