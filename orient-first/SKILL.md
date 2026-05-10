---
name: orient-first
description: Force orientation before any work begins. Activates at the start of any agent session to prevent premature "helping." Use when the user opens a new session, shares a vague idea, reports a bug, or asks to work on existing code.
---

# orient-first

**Keywords:** First Principles, Known Unknowns, Bounding Box, Session Charter, Stop and Think, Pragmatic Programmer

**When:** At the start of any agent session before writing, reading, or modifying code.

**Do:**
1. State the workflow mode: ideation | feature | bug | comprehension | modification
2. List what is KNOWN (facts, constraints, existing code)
3. List what is UNKNOWN (assumptions, missing context, risks)
4. Define the ONE bounded goal for this session
5. Explicitly state what is OUT OF SCOPE

**Stop:** Do not write code, create files, or explore the codebase beyond what is needed to answer the 5 items above. If the user input is a single vague sentence, ask clarifying questions before proceeding.
