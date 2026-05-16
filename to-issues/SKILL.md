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
3. List ALL files per slice: existing + new (include tests)
4. Check parallelism — zero file overlap = can run simultaneously
5. Create issues with: What to build, Acceptance criteria, Blocked by, Files, Can work parallely
6. Create in dependency order (blockers first)

**Stop:** No horizontal slices (one layer only). Every slice must be independently testable.
