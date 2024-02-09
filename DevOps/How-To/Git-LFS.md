# 1 Introduction

## 1.1 Documentation
- Manage large files in Git - https://docs.microsoft.com/en-us/azure/devops/repos/git/manage-large-files?view=azure-devops
- Install Git LFS - https://git-lfs.github.com/

## 1.2 When to Use
- Large File Storage **should not** be used to store static dependencies such as dlls and exes. These dependencies should be using either an internal project reference or use a package management solution, such as nuget, to handle download of these dependencies at build time
- LFS may be used for files that are media types

## 1.3 Before you start
- review the files that you would like to use LFS for, and selectively making sure the files that you will be storing in the git repo are absolutely required as large files for versioning
- organize these files in a manner that you will reference them in your application solution so they are easy to find

# 2 Using LFS

## references
- [Microsoft doc](https://docs.microsoft.com/en-us/azure/devops/repos/git/manage-large-files?view=azure-devops)
- [blog post](https://devblogs.microsoft.com/devops/announcing-git-lfs-on-all-vso-git-repos/)
- [Git LFS install](https://git-lfs.github.com/)

## Creating the git LFS repo

1. install git LFS locally following https://git-lfs.github.com/
1. Get Latest from TFS
1. navigate to desire repo location, initialize git
1. set upstream to the desire git repo url
1. add _.gitignore_ for Visual Studio
1. add lfs track extensions (this updates the _.gitattributes_ file)
1. commit and push _.gitignore_ and _.gitattributes_
1. stage, commit, and push files in chunks (you can do that in one push but the operation may time out if the request size is too large)

## Create the build pipeline

*ADO pipeline syntax*

``` yaml
variables:
  solution: '$(Pipeline.Workspace)/$(SolutionDir)'
  buildPlatform: 'Any CPU'
  buildConfiguration: 'Release'
```

There are two repositories to be cloned to do the build. In order to checkout two different repos, we have to add them under resources 
- set the repository resource

``` yaml
resources:
  repositories:
  - repository: Common
    type: git
    name: CommonLibraries
```

As stated above the checkout paths must match what are currently referenced inside the project.
- ref: https://docs.microsoft.com/en-us/azure/devops/pipelines/yaml-schema?view=azure-devops&tabs=example%2Cparameter-schema#checkout
- set the checkout path

``` yaml
  - checkout: self
    lfs: true
    path: LargeFilesPathName
  - checkout: Common
    lfs: true
    path: Commom/Libraries
```

Now we can do a build and publish

## 3.5 Developer workflow

### minimize file size as much as possible
1. clone _Common_ repo to _Common/Libraries_ with `--no-checkout`
1. checkout only the directory containing the files you need
1. clone _LargeFilesPathName_ repo with `--no-checkout`
1. checkout only the directory containing the files you need
1. branch _LargeFilesPathName_ from _main_ to local branch
1. navigate to the desire solution under LargeFilesPathName repo
  - modify, stage, commit, and push your changes

``` bash
git clone <url> Common/Libraries --no-checkout
git checkout main <path-to-files-you-need>

git clone <url> --no-checkout
git checkout main <path-to-files-you-need>
git branch -C youralias/yourbranchname
git checkout youralias/yourbranchname
```

### no one cares about file sizes
1. clone _Common_ repo to _Common/Libraries_
1. clone _LargeFilesPathName_ repo
1. branch _LargeFilesPathName_ from main to local branch
1. navigate to the desire solution under LargeFilesPathName repo
  - modify, stage, commit, and push your changes

``` bash
git clone <url> Common/Libraries

git clone <url>
git branch -C youralias/yourbranchname
git checkout youralias/yourbranchname
```
