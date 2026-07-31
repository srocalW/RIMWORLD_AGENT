# MODES.md

# Analysis Modes

This document defines **how the agent approaches a task**.

Rather than providing many fixed workflows, the agent selects:

- A **Task**
- An **Analysis Depth**

The workflow should adapt dynamically to the project, available evidence and the user's objective.

---

# Task

Choose the task that best matches the user's goal.

## Analyze

Understand, explain, or study the project.

Typical objectives include:

- Understanding a mod
- Learning implementation ideas
- Reverse engineering
- Studying architecture
- Exploring framework behavior

The emphasis is on understanding rather than solving a specific problem.

---

## Debug

Identify, verify and explain problems.

Typical objectives include:

- Exceptions
- Compatibility issues
- Unexpected behavior
- Runtime errors
- Performance regressions

The emphasis is on finding evidence, identifying root causes and proposing solutions.

---

# Analysis Depth

Analysis depth determines **how deeply the project should be investigated**, not how long the response should be.

Always begin with the shallowest depth that can answer the user's question.

Increase the depth only when additional evidence is required.

---

## Level 1 — Content

Goal:

Understand **what** the mod provides.

Focus on:

- Features
- Gameplay
- XML definitions
- Project structure
- Dependencies
- Public interfaces

Avoid unnecessary implementation details.

Stop when the user can clearly understand what the project does.

---

## Level 2 — Architecture

Goal:

Understand **how** the mod works.

Focus on:

- System architecture
- Module responsibilities
- Runtime flow
- Data flow
- Harmony patches
- XML ↔ Code interaction
- Representative implementations

Do not inspect every class.

Focus on explaining the design.

Stop when the overall implementation strategy is understood.

---

## Level 3 — Implementation

Goal:

Understand **how the implementation actually executes**.

Focus on:

- Decompiled source code
- Runtime call chains
- Harmony execution flow
- Critical algorithms
- Reflection
- Generic implementations
- Compiler-generated code
- Performance-critical logic

Investigate only details that support the current objective.

Avoid unnecessary exploration.

Stop when the required implementation details have been verified.

---

# Adaptive Depth

Analysis depth is dynamic.

Start with the minimum depth required.

Increase the depth only when:

- existing evidence is insufficient;
- runtime behavior cannot be explained;
- implementation details become relevant;
- the user explicitly requests deeper analysis.

Whenever the depth changes, briefly explain why.

Example:

Content

↓

Architecture

Reason:

Understanding the XML alone is insufficient to explain the runtime behavior.

---

# General Guidelines

Prefer understanding over exhaustive inspection.

Prefer representative implementations over every implementation.

Prefer evidence over assumptions.

Choose the simplest analysis depth that satisfies the user's objective.

Only investigate deeper layers when they provide meaningful additional insight.

A deeper analysis is not necessarily a better analysis.
