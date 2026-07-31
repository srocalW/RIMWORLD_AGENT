# TOOLS.md

# Tool Strategy

This document defines how the agent should discover, evaluate and use available tools.

The goal is not to maximize tool usage.

The goal is to use the **right tool for the current task**.

---

# General Principles

Tools exist to improve:

- accuracy
- efficiency
- reproducibility

Do not use tools simply because they are available.

Prefer the simplest tool that can provide reliable evidence.

---

# Capability Discovery

Before performing a task manually, determine whether the current workspace already provides an appropriate capability.

Possible capabilities include:

- VS Code extensions
- MCP servers
- Language servers
- Workspace scripts
- Build tools
- Decompilers
- Existing project documentation

Do not assume a capability exists.

Discover available capabilities first.

---

# Tool Priority

When multiple approaches are possible, prefer the following order.

1. Existing workspace capability

Examples:

- Language Server
- Project Index
- Workspace Script

---

2. Dedicated development tools

Examples:

- Decompiler
- MCP Server
- Git integration

---

3. Standard command-line tools

Examples:

- rg
- git
- dotnet
- PowerShell

---

4. Manual inspection

Read files manually only when automated capabilities are unavailable or unnecessary.

---

# Tool Selection

Choose tools according to the current objective.

Examples:

Project structure

→ Search / File Explorer

Implementation

→ Language Server / Decompiler

Runtime behavior

→ Debugger / Logs / Decompiled source

Dependencies

→ Project metadata

XML relationships

→ Search + XML inspection

Always explain why the chosen tool is appropriate.

---

# Extension & MCP Awareness

The workspace may provide extensions or MCP servers with capabilities beyond standard file inspection.

Examples include:

- DLL decompilation
- Symbol navigation
- API lookup
- Project indexing
- Framework documentation
- Repository search

Whenever such capabilities are available, consider using them before implementing equivalent functionality manually.

---

# Explain Before Action

Before invoking an important tool, briefly explain:

Purpose

Expected result

Workspace impact

This explanation should be concise.

---

# Safe Execution

Prefer read-only operations.

Avoid unnecessary:

- file modification
- file deletion
- package installation
- environment changes

Only perform write operations when they directly support the user's objective.

---

# Temporary Files

Temporary files are acceptable when they significantly improve analysis.

Whenever temporary files are created:

Record:

- filename
- purpose
- whether they can be safely removed

Summarize them in the final Workspace Journal.

---

# Workspace Changes

Keep workspace modifications minimal.

Whenever files are:

- created
- modified
- deleted
- generated

Record:

Reason

Impact

Revertability

Never hide workspace changes.

---

# Tool Failure

If a tool cannot be used:

Explain:

- what failed
- why (if known)
- impact
- alternative approach

Do not silently ignore failures.

---

# Fallback Strategy

When the preferred tool is unavailable:

Attempt another suitable capability.

Examples:

Language Server

↓

Decompiler

↓

Search

↓

Manual inspection

Choose the smallest fallback that still provides sufficient evidence.

---

# General Rules

Prefer existing capabilities over custom implementations.

Prefer evidence-producing tools over convenience tools.

Avoid repeating work that available tools can already perform.

Tool usage should always be transparent, purposeful and proportional to the current task.
