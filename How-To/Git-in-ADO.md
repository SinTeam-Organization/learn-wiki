[[_TOC_]]

# ADO

## 1.1 Navigate to the repo
- View repo - go to https://dev.azure.com/<repo>
- View branch - click on the branch dropdown and select _main_
- View commits - click on _History_ under _Files_
- Find file - type 'git' in the search bar next to the branch name
  - View file - select a file you'd like to view content
    - note you can view commit history, compare commits

## 1.2 Branch and Commit changes
- Branch - click on the branch dropdown and select _+New Branch_
  - Name the branch according to branch naming convention
  - Link a work item
    - you can do a search on the work item you'd like to attach to
- Create a file - under '/Sandbox/', create a new file
  - name the new file <alias>-newfile-ado.md
- Make a change - make a change in the editor (click _Edit_ within ADO if it is not already in edit mode)
- Commit a change - click _Commit_ in the editor > enter a meaningful comment > click _Commit_
- Pull Request - click _Create a Pull Request_ 
  - enter a meaningful Title on the change
  - enter a meaningful Description:
    - What is being reviewed here. What should the reviewers know. What was the change intent to accomplish. Any links to any tested builds should be included here
  - enter reviewers (enter at least one review who can review the change during this lab)
  - link a work item if there is no work items linked
  - click _Create_

## 1.3 Review a Pull Request
- View Pull Requests - go to https://dev.azure.com/<repo>/pullrequests?_a=mine > select your PR
  - Overview provides a summary information of the PR
- View changes - click on _Files_
  - This shows the diff of the PR
  - both _Updates_ and _Commits_ shows how the sausage is made
- Enter review comments - go back to _Files_
  - hover over the line of code you'd like to comment, and click the _comment_ icon
- Resolve a comment - go back to _Overview_
  - write a reply to an existing comment, click _Resolve_
  - _note: when there are unresolved comments, the requester of the PR should review the suggested changes with the reviewer, make the change, and resubmit the PR again on the same branch_

## 1.4 Complete a Pull Request
- Approve a PR - on the same PR, click _Approve_
  - required and optional reviewers will approve the change in this step
- Complete a PR - on the same PR, click _Complete_
  - _Merge (no fast forward)_ is the recommended option to ensure all history is recorded
  - you can choose to _Complete associated work items after merging_. However, if you will be submitting several PR on a user story, uncheck this option so the user story will not be closed once the PR is completed
  - _delete <branchname> after merging_ is recommended once the PR is done. This will ensure a new branch has to be created for new changes and requiring another pull from the main branch to pull in the latest code with changes made by others. Otherwise, you will have to make sure you do a pull from main, merge to your branch on your local repo before you can push new changes.
  - click _Complete merge_
- View PR commit history - go to the repo and main branch, note that under _History_ there is a commit titled 'Merged PR xxx'
