# Repository guidance

Before working, read these optional instruction files in order,
resolving these paths from this repository's root:

1. `.agents/organization/AGENTS.md`
2. `.agents/workspace/AGENTS.md`

Read each file if it resolves to a readable regular file.
Skip absent files; report broken or unreadable links.
Read each resolved file only once to avoid duplicate loading and cycles.

Resolve references inside imported files relative to their real target
directory after following symlinks.

Apply organization guidance, then workspace guidance, then the repository
instructions below. More specific applicable instructions take precedence.

## Repository scope

- This repository is the shared Molecule scenario harness vendored by the Moodle,
  PostgreSQL, KeyDB, and NFS Ansible operators.
- `default/` owns shared create/prepare/converge/verify/destroy behavior;
  `default/verify_tasks/<component>/` owns component assertions; `kind/` owns the
  disposable-cluster scenario.
- Scenario variables, file layout, and task names are interfaces to every consumer.
  Keep base lifecycle checks generic and component checks isolated.

## Validation

- Install the pinned dependencies from `requirements.txt`, lint YAML/Ansible, and
  execute `molecule test` through at least one affected operator consumer where
  this repository is mounted as `molecule/`.
- Molecule creates and destroys cluster resources. Confirm the disposable context
  before running it and preserve failure logs needed for diagnosis.
