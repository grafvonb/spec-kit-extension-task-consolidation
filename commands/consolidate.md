---
description: Consolidate an existing tasks.md into cohesive implementation outcomes without losing coverage or progress.
scripts:
  sh: ../../scripts/bash/check-prerequisites.sh --json --paths-only
  ps: ../../scripts/powershell/check-prerequisites.ps1 -Json -PathsOnly
  py: ../../scripts/python/check_prerequisites.py --json --paths-only
---

Aim for fewer manageable tasks and implementation iterations, without forcing a target count.

1. Consider `$ARGUMENTS`. Read `tasks.md`, `spec.md`, `plan.md`, project instructions,
   the constitution and available design artifacts. Reuse `FEATURE_DIR` from the current tasks run;
   otherwise run `{SCRIPT}` from the project root. If resolution fails or required
   inputs are ambiguous, missing, empty or unreadable, report it and stop unchanged.
2. Merge related work and remove proven duplication: repeated model edits, guards
   and enablement, and tests belonging to the same outcome are common candidates.
   Keep each task manageable for one focused implementation iteration. Split only
   clearly oversized tasks; do not add work or restructure an already reasonable list.
3. Preserve required work and details, tests and required test-first ordering,
   story/phase constraints, safe behavior, real dependencies and useful parallelism.
   Keep completed tasks, their IDs and evidence, and partial progress intact;
   never merge unfinished work into a checked task. Retain work if its necessity is uncertain.
4. Repair checklist IDs, references, dependencies, parallel examples and counts.
   Renumber fresh drafts; preserve surviving IDs on started or externally referenced
   lists and allocate new IDs above the original maximum. Keep `[P]` only where
   prerequisites and file conflicts allow it. Check coverage and save only `tasks.md`;
   leave it unchanged if no reasonable simplification or consistency repair is needed.

Report briefly: **Consolidated 14 → 10 tasks**, plus one sentence on the main changes,
using actual counts (or report no change). Mention unresolved issues without claiming tests passed.
As a hook, finish saving before returning to the parent for remaining hooks and completion.
Do not regenerate tasks, dispatch hooks, implement work, commit or publish. Report failures explicitly.
