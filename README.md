# GitHub Action workflows depending on each other

* A job can declare in `needs` one or more other jobs to be successful before running.
* The needed job must be in the same workflow (in the same YAML file).
* One can make the dependent job a reusable job by adding the trigger `workflow_call` and then make the dependencies call it.

* In our case the CI workflow runs first and then calls the Generate workflow

