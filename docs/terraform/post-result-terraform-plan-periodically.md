# Post the result of `terraform plan` to Slack channel periodically to check the divergence between State and real infrastructure

## Problem

If we run `terraform plan` with the option `-refresh=false` in CI to avoid the exceed of the API rate limit and speed up CI, sometimes we overlook the divergence between State and real infrastructure.

## How to solve

To find the divergence, let's prepare a periodical job to run `terraform plan` without the option [-refresh=false](https://www.terraform.io/docs/commands/plan.html#refresh-true) on the master branch and if there is a diff, post the result to the Slack channel.

When we find the post, we should fix the divergence manually.

## Implementation detail

- run `terraform plan -detailed-exitcode` without the option `-refresh=false` on the master branch and if there is a diff, post the result to the Slack channel.
  - We can judge whether there is a diff or not with the option [detailed-exitcode](https://www.terraform.io/docs/commands/plan.html#detailed-exitcode)
