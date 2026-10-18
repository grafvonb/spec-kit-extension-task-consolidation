# Task Consolidation

Reduce the number of tasks and later implementation iterations by merging work
that reasonably belongs together and removing duplication. Aim for fewer manageable
tasks without losing required work or forcing a particular count. Split only clearly
oversized tasks; leave already reasonable lists alone.

Requires an initialized Spec Kit project with an agent integration, standard
scripts, and existing `tasks.md`, `spec.md`, and `plan.md`. Spec Kit **1.2.1** is
the tested baseline; the manifest accepts `>=1.2.1,<1.3.0`.

## Install and migrate

From the target project's root, substitute your clone's absolute path:

```bash
# Only if the old preset is installed: remove it before adding the extension.
specify preset remove task-consolidation
specify extension add --dev /absolute/path/to/spec-kit-extension-task-consolidation
```

Confirm the generated tasks command no longer contains the preset wrapper,
including through other overrides. Keep exactly one consolidation hook.

**Hook order matters:** in `.specify/extensions.yml`, place the existing
`task-consolidation` entry first under `hooks.after_tasks`, before publish/commit
hooks. Keep it enabled, with `optional: false` and no non-empty `condition`.
Spec Kit 1.2.1's tasks template follows YAML order, skips non-empty conditions,
and does not sort by `priority`. Reinstallation can append the hook at the end:
recheck order after installation, reinstall, or other hook changes.

## Use

Run the official `speckit.tasks` as usual: it generates the draft, invokes and
waits for consolidation, handles remaining hooks, then reports completion.
The extension does not wrap, replace, or recursively invoke task generation.

For an existing or already-started list, invoke
`/speckit.task-consolidation.consolidate`, or
`$speckit-task-consolidation-consolidate` in Codex skills mode.
Only `tasks.md` changes. Required work, tests and test-first ordering, story/phase
constraints, dependencies, useful parallelism, and completed work are preserved.
Surviving IDs on started lists remain stable. Consolidation does not execute tasks
or their tests. The report stays short, for example:

> **Consolidated 14 → 10 tasks.** Combined related model edits and overlapping validation work.

## Reinstall or remove

Source edits do not update installed commands automatically. Reinstall with:

```bash
specify extension add --dev /absolute/path/to/spec-kit-extension-task-consolidation --force
```

Recheck hook order afterward. To uninstall:

```bash
specify extension remove task-consolidation
```

## Validation and limits

Spec Kit 1.2.1 installation, reinstall, removal and migration checks passed.
Earlier same-session trials covered execution, ordering, preservation and stability;
they predate this reduction-focused command. Its behavior has not been re-evaluated.
Independent agent sessions and PowerShell/Python execution remain untested.
Registration success alone does not prove behavioral effectiveness.

Execution is agent-driven. Mandatory hooks require actual invocation and waiting;
malformed hook YAML currently warns and allows the parent to continue. Correct
hook ordering must be established before running tasks.
