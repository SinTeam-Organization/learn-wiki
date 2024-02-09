[[_TOC_]]

# 1 Create a Test Branch
- navigate to branches https://dev.azure.com/FirstAmericanDBS/SearchTrax/_git/Wiki/branches
- click _New branch_
  - enter branch name _<alias>/test-branchpolicy_
  - _Create_

# 2 Create Branch Policy
- Once the branch is created
  - hover over the new test branch, select the context menu icon (verticle '...')
  - select _Branch policies_
    - ![image.png](/.attachments/image-93ef692a-e081-42a3-ac04-8e7f3641dcc4.png)

## 2.1 Turn on Policies
- Turn ON the following policies
  - _Require a minimum number of reviewers_
    - set the _minimum number of reviewers_ to 1
    - check _Allow requestors to approve their own changes_ if there is no one else to approve PRs in this lab
  - _Check for linked work items_
  - _Check for comment resolution_
- ![image.png](/.attachments/image-41f9af5b-de7b-47a7-b47e-c3492f87eb1b.png)

## 2.2 Turn on Build Validation
- Click + on _Build Validation_
- Add build policy
  - select "pass-build-policy-pipeline (Wiki)" on _Build pipeline_
  - add "/Sandbox/*" to _Path filter_
  - select _Automatic_ trigger
  - select _Required_ on _Policy requirement_
  - use default on Build expiration
  - enter "PR good build" in _Display name_
  - _Save_
- ![image.png](/.attachments/image-7eab1a24-4685-451a-9c19-40a80bafcdfa.png)

## 2.3 Add required reviewers
- Click + on _Automatically included reviewers_
  - Enter a name in Reviewers
  - Select _Required_
  - _For pull request affecting these folder_
    - you can specify a path in the repo that require this reviewer to approve. For mono-repos that contains multiple solutions, you may decide to use this filter to selectively assign required approvers
  - Uncheck _Allow requestors to approve their own changes_
    - _if there is not another person to approve the PR in this lab, Check this option_
- _Save_
- ![image.png](/.attachments/image-27f53ebc-44d9-4951-872f-ff3eac7ea8a6.png)

# 3 Create a test PR

## 3.1 Branch from the Test Branch
- Create a new branch from the Test Branch
  - go to branches https://dev.azure.com/FirstAmericanDBS/SearchTrax/_git/Wiki/branches
  - select your test branch _<alias>/test-branchpolicy_
  - on the branch dropdown > select _+ New Branch_
    - name the branch _<alias>/test-branchpolicy-newbranch_
    - _Create_

## 3.2 Modify a file
- In your new branch _<alias>/test-branchpolicy-newbranch_
- Modify the file _/Sandbox/PassTests/build-policy-test.md_
- Commit your changes
- Create a pull request
  - make sure to select the correct target branch where the branch policy is set
    - i.e. _<alias>/test-branchpolicy_
  - ![image.png](/.attachments/image-3a311756-4155-4f3a-8e88-9adf19301876.png)
  - _Create_

## 3.3 Complete the PR
- View the list of failed checks in the Overview page shown in the PR
- click _View all x checks_
  - Work items must be linked
  - required approver must approve
  - "PR good build" succeeded
  - Comment must be resolved
- ![image.png](/.attachments/image-e3da35bb-4a57-4552-862a-31676f34c447.png)

## 3.4 Update the PR, Set auto-complete
- Add a comment to the PR (ask the required approver to do so if available)
  - note that another check just failed
- select _Set auto-complete_
  - this will complete the PR as soon as all validations have passed
- Resolve comment
- Add a work item link
- Have required reviewer approve the PR
- _Note: when all validations have passed, the PR will be merge to the target branch_

# 4 Test a Failing build validation

## 4.1 Update the branch policy
- Navigate to branches https://dev.azure.com/FirstAmericanDBS/SearchTrax/_git/Wiki/branches
- Open the test branch named _<alias>/test-branchpolicy_
- Navigate to branch policies
- Add the following build validation
  - fail-build-policy-pipeline
  - /Sandbox/FailTests/*
  - Automatic trigger
  - Required Policy requirement
  - "PR bad build"
- _Save_
- ![image.png](/.attachments/image-6c0664a7-09f9-4faa-bf38-525ffc96e0f2.png)

Updated policy
- ![image.png](/.attachments/image-545d58df-f0d0-438d-bc10-786ee3656559.png)


## 4.2 Create a test PR

### Branch from the Test Branch
- Create a new branch from the Test Branch
  - go to branches https://dev.azure.com/FirstAmericanDBS/SearchTrax/_git/Wiki/branches
  - select your test branch _<alias>/test-branchpolicy_
  - on the branch dropdown > select _+ New Branch_
    - name the branch _<alias>/test-failpolicy_
    - _Create_

### Modify a file
- In your new branch _<alias>/test-failpolicy_
- Modify the file _/Sandbox/FailTests/build-policy-test.md_
- Commit your changes
- Create a pull request
  - make sure to select the correct target branch where the branch policy is set
    - i.e. _<alias>/test-branchpolicy_
  - ![image.png](/.attachments/image-41b22e5e-a89c-44f9-a1fa-d97aca1de6d2.png)
  - _Create_

### View the PR
- View the list of failed checks in the Overview page shown in the PR
- click _View all x checks_
  - Note that the PR bad build should fail
- This prevents the PR from completion
- ![image.png](/.attachments/image-1f2d1983-3c97-414d-a107-87835c7edfd5.png)