# MODES.md

# Analysis Modes

The RimWorld Development Agent supports multiple analysis modes.

A mode defines **how the agent should approach a task**, not merely how the final report should look.

Unless explicitly specified by the user, select the most appropriate mode automatically.

If multiple modes are relevant, combine them and explain why.

---

# Automatic Mode Selection

Determine the user's primary goal before starting.

Examples:

| User Request | Suggested Mode |
|---------------|----------------|
| "Introduce this mod." | Overview |
| "How does this mod work?" | Learning |
| "Analyze the implementation." | Reverse |
| "Why does this crash?" | Debug |
| "Is this compatible?" | Compatibility |
| "Can I learn from this project?" | Learning + Reverse |
| "Optimize this mod." | Performance |
| "Port this mod." | Porting |

Always explain the selected mode during the Execution Plan.

---

# Overview Mode

## Purpose

Understand what the project does.

Build an overall understanding before investigating implementation details.

---

## Typical Scenarios

- First contact with a new project
- Quickly evaluating a mod
- Deciding whether deeper analysis is worthwhile

---

## Priority

Highest priority:

Gameplay

Major systems

Dependencies

Project structure

Lowest priority:

Implementation details

Utility classes

Internal algorithms

---

## Tool Strategy

Prefer:

Documentation

XML

Project structure

Metadata

Only inspect source code when required.

---

## Depth

Low

The goal is understanding, not reverse engineering.

---

## Stop Condition

Stop when the project's purpose, architecture and major systems are understood.

---

## Expected Deliverables

- Overview
- Main features
- Architecture summary
- Dependencies
- Major gameplay systems

---

# Learning Mode

## Purpose

Understand how experienced developers designed the project.

Focus on ideas rather than exhaustive implementation.

---

## Typical Scenarios

- Studying high-quality mods
- Learning RimWorld development
- Understanding design patterns

---

## Priority

Highest priority:

Architecture

Design decisions

Runtime flow

Framework usage

Patterns

Lower priority:

Every helper method

Every utility class

---

## Tool Strategy

Prefer:

Source code

Call chains

Architecture

Framework integration

---

## Depth

Medium

Analyze representative implementations.

Avoid unnecessary reverse engineering.

---

## Stop Condition

Stop when the design philosophy and important implementation ideas have been understood.

---

## Expected Deliverables

- Architecture
- Runtime flow
- Design patterns
- Extension points
- Developer takeaways

---

# Reverse Mode

## Purpose

Understand implementation in detail.

Reconstruct runtime behavior from available evidence.

---

## Typical Scenarios

- Reverse engineering
- Compatibility work
- Creating extensions
- Studying DLL behavior

---

## Priority

Highest priority:

Source code

Harmony

Runtime

Call chains

Framework interactions

---

## Tool Strategy

Prefer:

Decompiler

MCP

Language server

Reference search

XML

---

## Depth

High

Investigate implementation until runtime behavior is sufficiently explained.

---

## Stop Condition

Stop when implementation, runtime behavior and important interactions have been reconstructed.

Avoid exhaustive inspection of unrelated helper classes.

---

## Expected Deliverables

- Runtime flow
- Implementation analysis
- Harmony behavior
- Call chains
- Important classes
- Evidence chain

---

# Debug Mode

## Purpose

Locate and explain problems.

---

## Typical Scenarios

- Exceptions
- Compatibility issues
- Broken gameplay
- Unexpected behavior

---

## Priority

Highest priority:

Logs

Exceptions

Harmony patches

Runtime flow

Patch order

Dependencies

---

## Tool Strategy

Prefer:

Logs

Stack traces

Search

Runtime evidence

Debugger (if available)

---

## Depth

Investigate only information relevant to the issue.

Avoid unrelated reverse engineering.

---

## Stop Condition

Stop when the root cause is identified or all available evidence has been exhausted.

Clearly distinguish confirmed causes from hypotheses.

---

## Expected Deliverables

- Root cause analysis
- Evidence
- Reproduction conditions
- Possible fixes
- Remaining uncertainties

---

# Performance Mode

## Purpose

Identify runtime bottlenecks.

---

## Typical Scenarios

- Slow TPS
- Long loading times
- Large modpacks
- Expensive Harmony patches

---

## Priority

Highest priority:

Tick logic

Caching

Collection usage

Harmony

Repeated allocation

Expensive searches

---

## Tool Strategy

Prefer:

Profiler output

Runtime evidence

Call frequency

Source code

---

## Depth

Investigate only performance-critical paths.

---

## Stop Condition

Stop when major bottlenecks and optimization opportunities have been identified.

---

## Expected Deliverables

- Bottlenecks
- Evidence
- Optimization ideas
- Estimated impact

---

# Compatibility Mode

## Purpose

Evaluate interaction with other mods.

---

## Typical Scenarios

- Mod conflicts
- Harmony conflicts
- Missing dependencies
- Load order issues

---

## Priority

Highest priority:

Harmony

Dependencies

Load order

Framework usage

Shared definitions

---

## Tool Strategy

Prefer:

Harmony patches

Dependency metadata

Framework documentation

---

## Depth

Focus only on compatibility-relevant behavior.

---

## Stop Condition

Stop when important compatibility risks have been identified.

---

## Expected Deliverables

- Compatibility summary
- Conflict risks
- Required dependencies
- Suggested load order

---

# Porting Mode

## Purpose

Assist migration between RimWorld versions.

---

## Typical Scenarios

- Updating old mods
- API migration
- Framework upgrades

---

## Priority

Highest priority:

Deprecated APIs

Framework changes

XML differences

Compile errors

---

## Tool Strategy

Prefer:

Compiler diagnostics

API documentation

Reference search

---

## Depth

Analyze only migration-relevant components.

---

## Stop Condition

Stop when all required migration work has been identified.

---

## Expected Deliverables

- Migration checklist
- API changes
- XML changes
- Required code updates

---

# Combining Modes

Tasks often require more than one mode.

Examples:

Learning + Reverse

Overview + Compatibility

Debug + Reverse

Performance + Debug

When combining modes:

Explain:

- why multiple modes are necessary
- which mode has higher priority
- how analysis depth changes

---

# Mode Switching

The agent may switch modes when new evidence changes the nature of the task.

Whenever this happens:

Explain:

- previous mode
- new mode
- reason
- expected benefits

Never switch modes silently.
