# GitHub Action workflows depending on each other

* A job can declare in `needs` one or more other jobs to be successful before running.
* In the CI.yaml file the `test` job depends on the `build` job. The `linter` job runs indpendently.


* The needed job must be in the same workflow (in the same YAML file) so the jobs in the generate.yaml file cannot depend the jobs in the `ci.yaml` file.
* However, One can make the `generate.yaml` workflow a **reusable workflow** by adding the trigger `workflow_call` and then make the dependencies call it.

* In our case the `ci.yaml` has an extra job called `run-generate` that depends on both the `linter` and the `test` jobs and runs the Generate workflow if both linter and test pass.
* Because the Generate workflow also has the `workflow_dispatch` trigger, one can run it from the GitHub UI in which case it will not "need" the CI job. Allowing this might or might not be a good idea.

