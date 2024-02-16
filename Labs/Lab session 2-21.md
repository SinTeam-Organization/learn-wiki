# Lab 2

As we are in these lab sessions, keep in mind how this work can integrate with other workstreams in terms of their automation.

## Session target format

- 30 min [max] walkthrough to provide an overview on how to achieve the objectives
- individual hands on and ask questions and collaborate
- screen share at the end on progress and learnings 

## Agenda

- Demo/walkthrough
- Objectives review
- Go do
- Screen share

Each person will select their own objective(s) to work on throughout the session. 

## Objectives

**Overall objective**

These objectives will be targeted towards getting AVD automated within a pipeline, but will not actually do the whole deployment. Each objective will not be dependent on one another and can be worked on independently. 

- Collaborate on the same repo with others - using **lab-sandbox**
  - create a feature branch
  - make changes and commit changes to your feature branch
  - create a Pull Request
  - have someone other than yourself to comment on your code inside the PR, then have the person approve the PR
  - view your changes in _main_ once the PR is complete
- Feature branch changes (modify an existing pipeline or create a new one)
  - anything from Lab 1, and/or
  - runs code scan with CodeQL
  - trigger a Secrets scan alert
  - trigger a Dependabot alert (this might take a bit more time to find a vulnerable dependency)
  - use the same parameters inside more than one job, and use the parameters to create conditional jobs (if yes then run else don't run)
  - create a pipeline with 1 build job, then 2 parallel test jobs, then 1 deploy job in the end in that order
  - add a job that runs another script file (e.g. az cli, powershell, etc.)
  - verify an output of an az cli produces the expected outcome

### Walk through

- Create a CI build on push
- Protect a branch with required reviewers and CI build pass
- Branch and create a Pull Request

### Resource

- [Collaborative development](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/getting-started/about-collaborative-development-models)
- [Recommended practices](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/getting-started/best-practices-for-pull-requests)
- [About branches](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-branches)
- [Merge conflicts](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts/about-merge-conflicts)
- [About PR merges](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/incorporating-changes-from-a-pull-request/about-pull-request-merges)
- [workflow syntax](https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions)

## Hand-holding

