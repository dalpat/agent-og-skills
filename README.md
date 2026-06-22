# Agent OG Skills

> Repo: `agent-og-skills` · install slug: `dalpat/agent-og-skills`. One project, one name — referred to as **Agent OG Skills** throughout.

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
- **Guardrails at known failure points** — Each skill targets a predictable failure mode in the SDLC (premature solving, XY problems, scope creep) and nudges the agent back on track when it triggers.

> **How skills fire (important):** A skill activates when the agent *matches its `description`* to the situation — it is model-invoked, not a guaranteed interrupt. If you need a behavior to run unconditionally (e.g. force `orient-first` at the start of every session), wire it as a **`SessionStart` hook**, not a skill. Skills are guardrails, not circuit breakers — they depend on the agent being healthy enough to route to them.

## Roadmap

Skills are organized by project phase. Status: ✅ Available | 🚧 Planned

### Phase 0: Problem Clarification
| Skill | Status | Trigger |
|-------|--------|---------|
| `orient-first` | ✅ | Force orientation before any work begins |
| `detect-xy` | ✅ | "Are you solving Y when the real problem is X?" |
| `ambiguity-detector` | 🚧 | "Where are you guessing instead of knowing?" |

### Phase 1: Ideation / Design
| Skill | Status | Trigger |
|-------|--------|---------|
| `grill-me` | 🚧 | Stress-test the plan, one question at a time |
| `enforce-contract` | 🚧 | Define pre/post-conditions for the solution |
| `simplify-enforcer` | 🚧 | "Is there a simpler way?" |

### Phase 2: Planning / Breakdown
| Skill | Status | Trigger |
|-------|--------|---------|
| `slice-session` | 🚧 | Force a single bounded task per session |
| `tracer-bullet` | 🚧 | "Build the thinnest end-to-end path first" |
| `write-prd` | ✅ | Create a PRD with user + developer stories |
| `to-issues` | ✅ | Break PRD into vertical slices with file tracking |

### Phase 3: Implementation
| Skill | Status | Trigger |
|-------|--------|---------|
| `tdd` | 🚧 | Red-green-refactor with vertical slices |
| `guard-hallucination` | 🚧 | Verify APIs/paths/facts before using them |
| `chunk-summarize` | 🚧 | When context grows, checkpoint and summarize |

### Phase 4: Review / Verification
| Skill | Status | Trigger |
|-------|--------|---------|
| `verify-output` | 🚧 | "Does this actually solve the stated problem?" |
| `guard-regression` | 🚧 | Re-run tests, diff output, catch non-determinism |
| `review-assumptions` | 🚧 | "What did you assume? Are those assumptions true?" |

### Phase 5: Handoff / State Preservation
| Skill | Status | Trigger |
|-------|--------|---------|
| `hydrate-context` | 🚧 | Load canonical state at session start |
| `snapshot-state` | 🚧 | Persist session state to canonical source |
| `update-adr` | 🚧 | Log irreversible decisions |
| `update-context` | 🚧 | Sharpen glossary, capture resolved terms |

### Phase 6: Completion or Dead End
| Skill | Status | Trigger |
|-------|--------|---------|
| `ship-it` | 🚧 | Acceptance criteria met? Merge. |
| `pivot-or-perish` | 🚧 | "Is this still worth pursuing?" |
| `archive-decision` | 🚧 | Log why this was abandoned |

## Installation

Install individual skills using the [Skills CLI](https://skills.sh/). Only ✅ Available skills can be installed:

```bash
npx skills add dalpat/agent-og-skills --skill orient-first
npx skills add dalpat/agent-og-skills --skill detect-xy
npx skills add dalpat/agent-og-skills --skill write-prd
npx skills add dalpat/agent-og-skills --skill to-issues
```

Or install globally:

```bash
npx skills add dalpat/agent-og-skills --skill orient-first -g -y
```

> Skills are plain `SKILL.md` files (frontmatter `name` + `description`, then the body). They also work with any agent that reads the SKILL.md format — e.g. drop a skill folder into `~/.config/opencode/skills/` for [opencode](https://opencode.ai), or `.claude/skills/` for Claude Code.

## Forcing a skill to always run (hooks)

A skill is *model-invoked* — it fires only when the agent matches its `description`. In practice that means subtle triggers can be missed entirely (e.g. an agent may answer an XY question directly instead of pausing). When a behavior must run **unconditionally**, inject it at session start instead of relying on activation.

`orient-first` ships with a ready-made example in [`hooks/`](./hooks):

**Claude Code** — wire the script as a `SessionStart` hook in `.claude/settings.json`:

```json
{
  "hooks": {
    "SessionStart": [
      { "hooks": [ { "type": "command",
          "command": "$CLAUDE_PROJECT_DIR/hooks/orient-first-session-start.sh" } ] }
    ]
  }
}
```

**opencode** — point the global `instructions` array at the directive in `~/.config/opencode/opencode.json`:

```json
{ "instructions": ["~/path/to/agent-og-skills/hooks/orient-first.directive.md"] }
```

Both inject the orientation directive into every new session, so the behavior runs even on a degraded or distracted agent. Use this pattern for any skill where a missed trigger is unacceptable.

## Contributing

Skills follow the **Incantation Format**:

1. **KEYWORDS** — Classic book terms the LLM knows (e.g., "Tracer Bullet", "Fail Fast")
2. **WHEN** — The exact trigger condition
3. **DO** — The precise behavior to execute
4. **STOP** — The hard boundary (what NOT to do)

Keep it under 150 words. No explanations the LLM already knows from its training.

## License

MIT
