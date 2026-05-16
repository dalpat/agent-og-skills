---
name: to-issues
description: Break a PRD into independently-grabbable GitHub issues using tracer-bullet vertical slices.
---

# to-issues

**Keywords:** Vertical Slice, Tracer Bullet, Issue Breakdown, Parallelism, Zero File Overlap, File Dependencies, Dependency Graph, Work Breakdown

**When:** User has a PRD and wants implementation tickets.

**Do:**
1. Fetch the PRD issue
2. Break into thin vertical slices — each cuts through ALL layers
3. For each slice, list ALL files: existing + new (include tests)
4. Design slices for parallelism — minimize file overlap so multiple agents can work simultaneously
5. Mark which slices have zero file overlap (can run in parallel) vs shared files (must serialize)
6. Create issues with: What to build, Acceptance criteria, Blocked by, Files, Can work parallely
7. Create in dependency order (blockers first)

**Stop:** No horizontal slices (one layer only). Every slice must be independently testable.
