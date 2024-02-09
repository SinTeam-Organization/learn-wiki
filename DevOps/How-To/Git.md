# 1 Introduction

*some notes were are writting for ADO, but the git stuff still applies.* 

## 1.1 Documentation

- https://git-scm.com/doc
- https://docs.microsoft.com/en-us/azure/devops/learn/git/what-is-git

## 1.2 Getting the code to the local machine for the first time

Before you can do a pull, you have to do a clone to setup the local repo before you start your work:
- clone

git command:
```bash
git clone <repourl>
```

## 1.3 Creating a branch

A branch should be used to house small, logical chunk of change (e.g. a feature) before it is merged back into the main branch. The goal is to group a set of changes that will make sense to someone during a code review, and if needed, revert as a single commit from the main branch.
- branch

A logical chunk of change
- include only the changes for the intended change. This could be a bug fix, a single functionality, or a small feature
- exclude any changes that are not part of the change. This could be a 'to-do' from another backlog item, a 'might-as-well' that isn't part of the current change, or a 'while-Im-here' that is from your past missed changes.

git command:
```bash
git branch -C <branchname>
```

## 1.4 Code change workflow in git

Developer makes changes to the code and commit the change to git by first getting the source code from the server to a local machine:
- pull > modify > stage > commit > push

| action | <div style="width:130px">location</div> |  |
|-------|--------------------|--------------------|
| pull | remote -> local | get the latest code base from the remote server (ADO git repo) onto the local machine (local git repo) |
| modify | local | do your thing, save your edits locally |
| stage | local | select the modified files that you would like to put in the commit queue. This is called 'staging your changes' |
| commit | local | once you have confirmed the desire files in stage is ready to be checked in. you then commit the staged changes. This creates a commit record for the change |
| push | local -> remote | once you have all the commits ready to be copied from the local git to the remote repo |

how it normally goes:
```bash
git status  # check the status of your local git repo
git pull    # get the latest from the server
git status
git add -A  # or adding only certain file - git add <list of files separated by a space>
git status
git commit -m "enter your meaningful commit message here"
git status
git push    # put your changes from local to remote
git status
```


## 1.5 Install and setup

- https://docs.microsoft.com/en-us/azure/devops/learn/git/install-and-set-up-git

# 2 Developer Tools

## 2.1 gitbash

gitbash is a console application that provides syntax coloring on git commands. It provides all functionality of git commands that you find in the git documentation. It is a useful tool to learn the various git commands without the limitation of a text editor extension or UI. The console also offers helpful tips on how to use a command when it is not able to process what you had entered.

## 2.2 Visual Studio Code

There are extensions you can add to make your life easier to pull and push code within VS Code's terminal. You can also add a bash console (using the gitbash.exe) to invoke git commands directly in VS Code.

## 2.3 Visual Studio IDE

If you are more of a UI user rather than a command line user, there is an ADO git interface in Visual Studio IDE that you can click on to do branching, pull, and push. However, some of the UI terms do not correspond directly to a single git command (e.g. Sync is a pull/push). So it is important to understand what each interface would do in terms of git commands that it will invoke so you don't end up in a situation where the outcome of a merge/push is not what you expected.

# 3 Git tips
## 3.1 Common commands

These are the set of git commands that is used for majority of the development work.

| <div style="width:180px">command</div> | usage | notes |
|--|--|--|
|`git status`| view the status of the current repo including modified files, staged changes, and commit status | Always do a git status before staging, commit, or push. It will give you a good idea on what files are in modified state, what files are staged, what files are committed |
|`git clone`| cloning a copy of the source code from remote to local repo | See [Authentication](/DevOps/How-To/Git#3.2-authentication) section below for connecting to the remote repo |
|`git pull`| pulling the latest source code from the remote branch to local repo | Always pull the latest from remote repo before committing any change to reduce merge conflicts |
|`git add`| staging code changes ready for a commit | You can use `git add <file1> <file2>` for selected files, or use `git add *` to stage all modified files |
|`git commit -m "<comment>"`| commit staged changes to the local repo with a comment | always comment your commits so others know what you did in the change |
|`git push`| push committed changes from the local repo to the remote repo ||
|`git diff`| view the diffs of modified files before you stage them ||

## 3.2 Authentication 

### using Windows auth
If you are already logged in as a Windows user, you can clone from the remote repo without special auth steps if the repo uses a corporate login

```bash
git clone https://github.com/SinTeam-Organization/missionlz.git
```

### using SSH Key
There is an option to use SSH Key to authenticate with the remote repo following the article below. This can be used when you are not logged in as a Windows user, or if you are having issue using Windows auth
- https://docs.microsoft.com/en-us/azure/devops/repos/git/use-ssh-keys-to-authenticate?view=azure-devops

```bash
git clone git@github.com:SinTeam-Organization/missionlz.git
```

### changing remote repo
*use git remote*

```bash
git remote add origin git@github.com:SinTeam-Organization/missionlz.git
git pull
```
