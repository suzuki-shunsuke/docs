# Wait CI until CI on master is finished

## Current problem

### Case 1

1. CI on master branch is run
2. merge master branch to feature branch
3. `terraform plan` is run on the feature branch
4. `terraform apply` is run on master branch

In this case, the result of `terraform plan` on master branch is included in the result of `terraform plan` on the feature branch (step 3)

### Case 2

1. PR A which creates the resource A is merged to master branch
2. PR B which creates the resource B is merged to master branch
3. `terraform apply` is run on CI for PR B and resource A and B are created
4. `terraform apply` is run on CI for PR A and resource B are destroyed

## Solution

Wait CI until CI on master is finished before `terraform plan` is run.

https://circleci.com/docs/api/#recent-builds-for-a-single-project

CircleCI Personal API Token is needed.
