# Workflow - Gitflow


The project uses `Gitflow` workflow.


Gitflow Workflow is a Git workflow design that was first published and made popular by [Vincent Driessen](https://nvie.com/posts/a-successful-git-branching-model/). The Gitflow Workflow defines a strict branching model designed around the project release.

See also [here](https://jeffkreeftmeijer.com/git-flow/).

# Usage


* Regular git commands
* git-flow [extensions](https://github.com/nvie/gitflow/wiki/Installation) - active fork (e.g. used for debians git-flow package) see [here](https://github.com/petervanderdoes/gitflow-avh/wiki)


# Commands


## QuickRef

### Initialize

gitflow | git
--------|-----
`git flow init` | `git init`
&nbsp; | `git commit --allow-empty -m "Initial commit"`
&nbsp; | `git checkout -b develop master`


### Connect to the remote repository

gitflow | git
--------|-----
_N/A_ | `git remote add origin git@github.com:MYACCOUNT/MYREPO`


### Features

#### Create a feature branch

gitflow | git
--------|-----
`git flow feature start MYFEATURE` | `git checkout -b feature/MYFEATURE develop`


#### Share a feature branch

gitflow | git
--------|-----
`git flow feature publish MYFEATURE` | `git checkout feature/MYFEATURE`
&nbsp; | `git push origin feature/MYFEATURE`


#### Get latest for a feature branch

gitflow | git
--------|-----
`git flow feature pull origin MYFEATURE` | `git checkout feature/MYFEATURE`
&nbsp; | `git pull --rebase origin feature/MYFEATURE`


#### Finalize a feature branch

gitflow | git
--------|-----
`git flow feature finish MYFEATURE` | `git checkout develop`
&nbsp; | `git merge --no-ff feature/MYFEATURE`
&nbsp; | `git branch -d feature/MYFEATURE`


#### Push the merged feature branch

gitflow | git
--------|-----
_N/A_ | `git push origin develop`
&nbsp; | `git push origin :feature/MYFEATURE` _(if pushed)_


### Releases

#### Create a release branch

gitflow | git
--------|-----
`git flow release start 1.2.0` | `git checkout -b release/1.2.0 develop`


#### Share a release branch

gitflow | git
--------|-----
`git flow release publish 1.2.0` | `git checkout release/1.2.0`
&nbsp; | `git push origin release/1.2.0`


#### Get latest for a release branch

gitflow | git
--------|-----
_N/A_ | `git checkout release/1.2.0`
&nbsp; | `git pull --rebase origin release/1.2.0`


#### Finalize a release branch

gitflow | git
--------|-----
`git flow release finish 1.2.0` | `git checkout master`
&nbsp; | `git merge --no-ff release/1.2.0`
&nbsp; | `git tag -a 1.2.0`
&nbsp; | `git checkout develop`
&nbsp; | `git merge --no-ff release/1.2.0`
&nbsp; | `git branch -d release/1.2.0`


#### Push the merged feature branch

gitflow | git
--------|-----
_N/A_ | `git push origin master`
&nbsp; | `git push origin develop`
&nbsp; | `git push origin --tags`
&nbsp; | `git push origin :release/1.2.0` _(if pushed)_


### Hotfixes

#### Create a hotfix branch

gitflow | git
--------|-----
`git flow hotfix start 1.2.1 [commit]` | `git checkout -b hotfix/1.2.1 [commit]`


#### Finalize a hotfix branch

gitflow | git
--------|-----
`git flow hotfix finish 1.2.1` | `git checkout master`
&nbsp; | `git merge --no-ff hotfix/1.2.1`
&nbsp; | `git tag -a 1.2.1`
&nbsp; | `git checkout develop`
&nbsp; | `git merge --no-ff hotfix/1.2.1`
&nbsp; | `git branch -d hotfix/1.2.1`


#### Push the merged hotfix branch

gitflow | git
--------|-----
_N/A_ | `git push origin master`
&nbsp; | `git push origin develop`
&nbsp; | `git push origin --tags`
&nbsp; | `git push origin :hotfix/1.2.1` _(if pushed)_



## Init


You can start using git-flow in your repository by using it’s init command.

`$ git flow init`


    Which branch should be used for bringing forth production releases? 
    - master    
    Branch name for production releases: [master] 
    Branch name for "next release" development: [develop] 
    How to name your supporting branch prefixes?    
    Feature branches? [feature/] 
    Bugfix branches? [bugfix/] 
    Release branches? [release/] 
    Hotfix branches? [hotfix/] 
    Support branches? [support/] 
    Version tag prefix? [] 
    Hooks and filters directory? [/home/benny/git-repos/mvntestapp/.git/hooks] 

git-flow is just a wrapper around existing git commands, so the init command doesn’t change anything in your repository other than creating branches for you. If you don’t want to use git-flow anymore, there’s nothing to change or remove, you just stop using the git-flow commands.

If you run git branch after setting up, you’ll notice that you switched from the master branch to a new one named develop.


## Features

* Feature branches may branch off from `develop`. 
* Must merge back into `develop`.


Feature branches are used to develop new features for the upcoming or a distant future release.

Feature branches typically exist in developer repos only, not in origin.


### Start a new Feature

1. **Plain git**

    `$ git checkout -b myfeature develop`

    Switched to a new branch "myfeature"


2. **git-flow**

    `$ git flow feature start myfeature`

    Switched to a new branch 'feature/myfeature'    
    Summary of actions:    
    - A new branch 'feature/myfeature' was created, based on 'develop'    
    - You are now on branch 'feature/myfeature'    
    Now, start committing on your feature. When done, use:    
     git flow feature finish myfeature    


### Publish a Feature

You can publish a feature to the remote server. So it can be used by other users. 


1. **Plain git**

    `$ git checkout feature/myfeature develop`

    Switched to branch 'feature/myfeature'

    `$ git push origin feature/myfeature`

2. **git-flow**

    `$ git flow feature publish myfeature`


### Finish up a Feautre

1. **Plain git**

    `$ git checkout develop`

    Switched to branch 'develop'

    `$ git merge --no-ff myfeature`

    Updating ea1b82a..05e9557

    (Summary of changes)

    `$ git branch -d myfeature` 

    Deleted branch myfeature (was 05e9557).


2. **git-flow**

    `$ git flow feature finish myfeature`

    Switched to branch 'develop'    
    Updating 9060376..00bafe4    
    Fast-forward    
    myfeature.txt | 1 +    
    1 file changed, 1 insertion(+)    
    create mode 100644 myfeature.txt    
    Deleted branch feature/myfeature (was 00bafe4).

    Summary of actions:    
    - The feature branch 'feature/myfeature' was merged into 'develop' 
    - Feature branch 'feature/myfeature' has been removed  
    - You are now on branch 'develop'   


### Make your Feature available on the remote repository

`$ git push origin develop`

`$ git push origin :feature/MYFEATURE` _(if published)_


## Releases


* Release branches may branch off from `develop`.
* Must merge back into `develop and master`.

Release branches support preparation of a new production release. They allow for minor bug fixes and preparing meta-data for a release (version number, build dates, etc.).


### Start a Release


1. **Plain git**

    `$ git checkout -b release-1.2 develop`

    Switched to a new branch "release-1.2"

2. **git-flow**

    `$ git flow release start 1.2`

    Switched to a new branch 'release/1.2'

    Summary of actions:     
    - A new branch 'release/1.2' was created, based on 'develop'  
    - You are now on branch 'release/1.2' 

    Follow-up actions:  
    - Bump the version number now!  
    - Start committing last-minute fixes in preparing your release  
    - When done, run:   
        git flow release finish '1.2'     


### Publish a Release

You can publish a release branch to the remote server. So it can be used by other users.

It's wise to publish the release branch after creating it to allow release commits by other developers.

1. **Plain git**

    `$ git checkout release/1.2`

 	`$ git push origin release/1.2`

2. **git-flow**

    `$ git flow release publish 1.2`



### Finish up a Release


1. **Plain git**

    `$ git checkout master`

    Switched to branch 'master'

    `$ git merge --no-ff release-1.2`
    
    Merge made by recursive.    
    (Summary of changes)

    `$ git tag -a 1.2`

    `$ git checkout develop`

    Switched to branch 'develop'

    `$ git merge --no-ff release-1.2`

    Merge made by recursive.    
    (Summary of changes)

    `$ git branch -d release-1.2`

    Deleted branch release-1.2 (was ff452fe).


2. **git-flow**

    `$ git flow release finish 0.1.0`

    Switched to branch 'master'     
    Merge made by the 'recursive' strategy.  
    myfile.txt | 1 +        
     1 file changed, 1 insertion(+)         
     create mode 100644 myfile.txt      
    Deleted branch release/1.2 (was 1b26f7c).

    Summary of actions:     
    - Latest objects have been fetched from 'origin'    
    - Release branch has been merged into 'master'  
    - The release was tagged '1.2'    
    - Release branch has been back-merged into 'develop'    
    - Release branch 'release/1.2' has been deleted   


### Make the Release available on the remote repository


`$ git push origin master`

`$ git push origin develop`

`$ git push origin --tags`

`$ git push origin :release/1.2` _(if published)_



## Hotfixes

* Hotfix branches may branch off from `master`.
* Must merge back into `develop and master`.

Hotfix branches are a lot like release branches, except they’re based on master instead of develop.

Because you keep your master branch always in sync with the code that’s on production, you’ll be able to quickly fix any issues on production.


### Start a Hotfix

1. **Plain git**

    `$ git checkout -b hotfix-1.2.1 master`

    Switched to a new branch "hotfix-1.2.1"

2. **git-flow**

    `$ git flow hotfix start 1.2.1`

    Switched to a new branch 'hotfix/1.2.1'    

    Summary of actions:     
    - A new branch 'hotfix/1.2.1' was created, based on 'master'   
    - You are now on branch 'hotfix/1.2.1'     

    Follow-up actions:      
    - Bump the version number now!      
    - Start committing your hot fixes       
    - When done, run:       

      git flow hotfix finish '1.2.1'



### Finish a Hotfix

1. **Plain git**

    `$ git checkout master`

    Switched to branch 'master'     

    `$ git merge --no-ff hotfix-1.2.1`

    Merge made by recursive.    
    (Summary of changes)

    `$ git tag -a 1.2.1`

    `$ git checkout develop`

    Switched to branch 'develop'

    `$ git merge --no-ff hotfix-1.2.1`

    Merge made by recursive.    
    (Summary of changes)

    `$ git branch -d hotfix-1.2.1` 

    Deleted branch hotfix-1.2.1 (was abbe5d6).

2. **git-flow**

    `$ git flow hotfix finish 1.2.1`

    Switched to branch 'master'     
    Merge made by the 'recursive' strategy.     
     myfix.txt | 1 +       
     1 file changed, 1 insertion(+)     
     create mode 100644 myfix.txt      
    Switched to branch 'develop'        
    Merge made by the 'recursive' strategy.     
     myfix.txt | 1 +       
     1 file changed, 1 insertion(+)     
     create mode 100644 assets.txt      
    Deleted branch hotfix/1.2.1 (was 08edb94).     

    Summary of actions:
    - Latest objects have been fetched from 'origin'        
    - Hotfix branch has been merged into 'master'       
    - The hotfix was tagged '1.2.1'     
    - Hotfix branch has been back-merged into 'develop'     
    - Hotfix branch 'hotfix/1.2.1' has been deleted        



### Make the Hotfix available on the remote repository


`$ git push origin master`

`$ git push origin develop`

`$ git push origin --tags`

`$ git push origin :hotfix/1.2.1` _(if published)_



## Support Branches

The idea of Support branches is to support previous releases. It may be difficult to hotfix a 1.0 when you already have 2.0 and 3.0 in master. In some cases you may not need that hotfix in 2.0 or 3.0 either.

For details see [here](https://github.com/petervanderdoes/gitflow-avh/wiki/Reference:-git-flow-support).