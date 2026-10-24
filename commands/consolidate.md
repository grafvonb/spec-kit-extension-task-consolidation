---
description: Consolidate an existing tasks.md into cohesive implementation outcomes through code-grounded review, without losing coverage or progress.
scripts:
  sh: ../../scripts/bash/check-prerequisites.sh --json --paths-only
  ps: ../../scripts/powershell/check-prerequisites.ps1 -Json -PathsOnly
  py: ../../scripts/python/check_prerequisites.py --json --paths-only
---

Aim for fewer manageable implementation tasks without forcing a target count. Preserve architectural boundaries in code; they need not become task boundaries.

1. Consider `$ARGUMENTS`. Read `tasks.md`, `spec.md`, `plan.md`, project instructions,
   the constitution, relevant design artifacts and progress records. Reuse `FEATURE_DIR`
   from the current tasks run; otherwise run `{SCRIPT}` from the project root.
   If resolution fails or required inputs are ambiguous, missing, empty or unreadable,
   report it and stop unchanged.

2. Ground the review in code. Inspect relevant implementations, interfaces, callers,
   reusable helpers and nearby tests. Identify each task’s outcome, dependencies,
   validation and acceptance obligations. Distinguish substantial new behavior from
   thin mapping, delegation or wiring; find shared contracts, fixtures and repeated edits.
   Do not treat the existing decomposition or earlier review as proof of necessity.
   If relevant code is unavailable, disclose the limitation and preserve uncertain work.

3. Evaluate every adjacent boundary and nonadjacent tasks sharing underlying behavior.
   Explicitly consider merging:
   - A service operation with its thin facade or mapping.
   - Input validation with frozen-request and preview/report logic.
   - Interface changes with implementations and required test doubles.
   - Single-item and collection workflows that would otherwise duplicate work.
   - Implementation with its fixtures, tests, formatting and documentation.
   - Repeated setup, guards, temporary enablement or integration repairs.

   For each plausible merge, identify the handoff or repeated work removed and whether
   the combined implementation **and validation** fit one focused iteration. Cite relevant
   code paths or symbols. Separate files, packages, layers, independent testability or
   hypothetical parallelism alone do not justify separate tasks.

4. Merge around cohesive, verifiable outcomes. Retain boundaries for concrete complexity,
   actual execution constraints or useful independent delivery—not vague “different concerns”
   or file counts. Recheck the result for remaining thin tasks and oversized combinations,
   especially protocol, concurrency, lifecycle and diagnostic work.
   Do not add scope or force restructuring. A no-change result requires explaining the
   strongest plausible merge and the code-grounded reason for rejecting it.

5. Preserve all requirements, invariants, compatibility, meaningful tests, required
   test-first ordering, story/phase constraints and real dependencies. Reuse fixtures
   without weakening boundary checks: unit or renderer tests cannot replace required
   command, terminal, logging or exit-path tests. Avoid duplicate implementations and
   unnecessary test cross-products.

   Keep completed tasks, IDs, evidence and partial progress intact; never merge unfinished
   work into a checked task. Retain work whose necessity is uncertain.

6. Repair IDs, references, dependencies, story ownership, parallel examples and counts.
   Check external references before renumbering. Renumber fresh drafts; preserve surviving
   IDs on started or externally referenced lists and allocate new IDs above the original
   maximum. Record superseded-ID mappings where needed. Keep `[P]` only where prerequisites
   and file conflicts permit it.

   Verify every original obligation still has an owner, dependencies and references are
   coherent, and progress is preserved. Check links and whitespace; do not run application
   tests merely to revise planning documents. Save only `tasks.md`, with concise reasons
   for important merges and retained boundaries. Leave it unchanged when no justified
   simplification or consistency repair is needed.

Report actual counts, such as **Consolidated 14 → 10 tasks**, the main merges and the
most consequential retained boundary. For no change, explain the strongest rejected merge.
Briefly identify code inspected, coverage/reference checks and unresolved limitations.
Do not equate fewer tasks with reduced scope or claim implementation tests passed.

As a hook, finish saving before returning to the parent for remaining hooks and completion.
Do not regenerate tasks, dispatch hooks, implement work, commit or publish. Report failures explicitly.