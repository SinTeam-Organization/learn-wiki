# Git with gitbash

**needs a rewrite for github**

## 1.1 Install git
Follow the link below to install and setup git (Windows/Mac)
- https://docs.microsoft.com/en-us/azure/devops/learn/git/install-and-set-up-git 

git install is required no matter which tool you are using to make your changes. Different tools will provide different interfaces to invoke git commands to accomplish the desire repo action.

In this lab, we will get familiar with using git commands no matter what editing tools or IDE you are using.

![image.png](/.attachments/image-001e7c81-f95f-49ea-8c3f-d0306e86dace.png)

## 1.2 Create source code directory, Clone repo

Before you can do any development work, the repo must be cloned from the remote git down to the local machine. The clone operation establishes the remote repo url for which the local repo is linked to when pushing changes.

_git-bash_ is part of the git install. It is a command console that accepts git commands in bash.
- open _git-bash_
- navigate to the directory that you will put your local git repos
  - create a sandbox directory
  - `cd /c/users/<alias>/documents`
  - `mkdir sandbox` (using _/c/users/msin/documents/sandbox_ in this example)
  - `cd sandbox`
- `git clone <repourl>`
  - you can copy the clone url from Github by
    - go to the repo in github
    - click the _Clone_ button
    - copy the https url
  - if you run `ls`, you will see <reponame>
- navigate to the repo directory 
  - `cd <reponame>`
  - note that in gitbash, the branch name is shown at the end
  - ![image.png](/.attachments/image-644b69c9-d4b4-4c96-8401-e34de07b3eda.png)

## 1.3 Branch for a logical chunk of change

The main (master) branch is normally protected and does not allow changes to be committed directly. The best practice is to enforce a Pull Request to ensure code changes are reviewed before they are merged to the main (master) branch. 

- `git branch <alias>/lab-addfile`
  - you can run `git branch -?` to view options (_note -? is not a valid switch but will bring up the usage menu_)
- `git branch`
  - this will show you the branches you now have on your local machine
  - ![image.png](/.attachments/image-b501d3b0-44f4-47c6-ac1f-0250fea54d46.png)
- `git checkout <alias>/lab-addfile`
  - this updates the file content in the directory from the previous branch (master) to the new branch
  - ![image.png](/.attachments/image-a6efc5f8-73f8-4068-9165-b9d6cf01eada.png)
  - you can switch between different branches locally by running `git checkout <branchname>`, and your changes in the local branch will not be overwritten just because you had switched to another branch

## 1.4 Commit a change to the local repo 
Now that you are in your developer branch, proceed to make the changes you would like to commit.

- add a new file under the Sandbox directory in the SearchTrax repo and name it _<alias>-myfile.md_
  - ![image.png](/.attachments/image-69226845-731e-497c-9da3-31446484cc69.png)
  - add any content to the file and save
- `git status`
  - this will show you files that are modified but have not yet been staged for a commit
  - ![image.png](/.attachments/image-396e79b5-9b9d-40d4-9472-307d924b7fe1.png)
- `git add *`
  - this will stage all of the modified files
  - you can also do `git add <file1> <file2>` to add only the files you'd like to stage
  - use quotes " around file names with spaces
- `git status`
  - this shows the files that are now staged for a commit
  - ![image.png](/.attachments/image-d95ec066-7081-47bf-bd85-9fe47f042236.png)
  - you can repeat your changes and stage them many times before a commit
- `git commit -m "adding new files in sandbox"`
  - changes are now moved from staged to committed to your local repo
  - ![image.png](/.attachments/image-746f6fa0-74ab-4185-b686-d3e6e491883f.png)
- `git status`
  - it shows there is nothing left to be committed
  - ![image.png](/.attachments/image-16087810-f6e8-4b0e-9535-b8f31505a885.png)

## 1.5 Push commits from local repo to remote git repo (ADO)
When you are pushing a local branch to the remote branch for the first time, there is no remote branch to push to. So there are a few extra steps that _git-bash_ will help you with getting your code to the remote branch.

If you check the remote repo in ADO at this time, you will not find your branch under that repo. This branch is residing on your local machine only. After you complete this exercise, you will see the remote repo in ADO will now have your new branch.

- `git push`
  - this will tell you that there is no upstream repo to push to, once you set the upstream repo, you will not need to run the following command again
  - ![image.png](/.attachments/image-305e07ac-473e-42b3-8bfc-39d44cefc22f.png)
- `git push --set-upstream origin <alias>/lab-addfile`
  - your changes are now pushed to the remote repo
  - ![image.png](/.attachments/image-d4f1219d-6779-4165-b725-e0e7ddbd4d64.png)

Make another change to the same file and commit the change locally, then push that to the remote repo again.

- modify your new file _<alias>-myfile.md_, Save changes
- `git status` - showing modified file
- `git add *` - stage modified files
- `git status` - showing staged files
- `git commit -m "comment">` - commit staged files with comment
- `git status` - showing nothing more to commit
- `git push` - push commit from local repo to remote repo

## 1.6 Verify changes are pushed to remote repo
Now you should see your branch showing in the ADO git repo

- view all branches
  - you should see that your branch has been added to the list
  - ![image.png](/.attachments/image-2a13e1a4-46d8-4229-8600-8c33da55fb71.png)
- go to 
  - on this page, you may see the following message to create a pull request
  - ![image.png](/.attachments/image-c3e61514-ef83-4bab-8679-ca8f28736835.png)
- create a Pull Request
  - at this point, you should have completed the [Git in ADO](/DevOps/Labs/Git-in-ADO#1.2-branch-and-commit-changes) Lab where it will show you how to complete a PR to merge your changes to the main (master) branch
  



