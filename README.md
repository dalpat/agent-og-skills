# Agent OG Skills

A collection of **micro-skills** for AI agents, grounded in timeless software engineering principles. Each skill is a tiny, composable behavioral trigger — not a lecture.

## Why Micro-Skills?

Modern LLMs are trained on the classics: *The Pragmatic Programmer*, *Clean Code*, *Refactoring*, *Design Patterns*, *The Mythical Man-Month*. They already know these concepts. What they need is **activation** — a precise keyword hook that triggers the right behavior at the right moment.

Instead of bloated skill files that explain what the LLM already knows, each skill here follows the **Incantation Format**:

```
1. KEYWORDS (the hooks)
2. WHEN (the trigger condition)
3. DO (the exact behavior)
4. STOP (the boundary)
```

**Target: 50-150 words.** If it's longer, it's not a micro-skill.

## Principles

- **Opt-in, not opt-out** — Only pay the context cost for skills you need in a session.
- **Composable** — Chain skills like Unix pipes: `orient-first | tracer-bullet | guard-hallucination`
- **Testable** — Each skill is small enough to validate independently.
- **Language/Stack Agnostic** — A `fail-fast` skill works for Python, React, or infrastructure.
- **Agent-Resilient** — Even if the main agent degrades, a micro-skill invoked at the right moment acts as a circuit breaker.

## The Lifecycle

These skills map to the entire AI-assisted project lifecycle:

```
0. PROBLEM CLARIFICATION
   ├─ orient-first         Force orientation before any work begins
   ├─ detect-xy            "Are you solving Y when the real problem is X?"
   └─ ambiguity-detector   "Where are you guessing instead of knowing?"

1. IDEATION / DESIGN
   ├─ grill-me             Stress-test the plan, one question at a time
   ├─ enforce-contract     Define pre/post-conditions for the solution
   └─ simplify-enforcer    "Is there a simpler way? Have you considered...?"

2. PLANNING / BREAKDOWN
   ├─ slice-session        Force a single bounded task per session
   ├─ tracer-bullet        "Build the thinnest end-to-end path first"
   └─ to-issues            Break into vertical slices

3. IMPLEMENTATION
   ├─ tdd                  Red-green-refactor with vertical slices
   ├─ enforce-contract     Re-assert contracts at function boundaries
   ├─ guard-hallucination  Verify APIs/paths/facts before using them
   └─ chunk-summarize      When context grows, checkpoint and summarize

4. REVIEW / VERIFICATION
   ├─ verify-output        "Does this actually solve the stated problem?"
   ├─ guard-regression     Re-run tests, diff output, catch non-determinism
   └─ review-assumptions   "What did you assume? Are those assumptions true?"

5. HANDOFF / STATE PRESERVATION
   ├─ hydrate-context      Load canonical state at session start
   ├─ snapshot-state       Persist session state to canonical source
   ├─ update-adr           Log irreversible decisions
   └─ update-context       Sharpen glossary, capture resolved terms

6. COMPLETION OR DEAD END
   ├─ ship-it              Acceptance criteria met? Merge.
   ├─ pivot-or-perish      "Is this still worth pursuing?"
   └─ archive-decision     Log why this was abandoned
```

## Installation

Install individual skills using the [Skills CLI](https://skills.sh/):

```bash
npx skills add dalpat/agent-og-skills --skill orient-first
npx skills add dalpat/agent-og-skills --skill guard-hallucination
npx skills add dalpat/agent-og-skills --skill tracer-bullet
```

Or install globally:

```bash
npx skills add dalpat/agent-og-skills --skill orient-first -g -y
```

## Contributing

Skills follow the **Incantation Format**:

1. **KEYWORDS** — Classic book terms the LLM knows (e.g., "Tracer Bullet", "Fail Fast")
2. **WHEN** — The exact trigger condition
3. **DO** — The precise behavior to execute
4. **STOP** — The hard boundary (what NOT to do)

Keep it under 150 words. No explanations the LLM already knows from its training.

## License

MIT
