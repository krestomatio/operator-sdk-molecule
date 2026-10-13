# Repository guidance

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
