# Adding Features



## Doing work on a feature branch

command | comment
--------|-----
`git flow feature start MYFEATURE` | creates the feature branch
_your stuff_ | do some fancy work
`git commit -a -m "your final commit message"` | commit your stuff to local repository
`git flow feature finish MYFEATURE` | closes the branch
`git push origin develop` | Push the merged feature branch to remote



## Doing work on a _public_ feature branch

command | comment
--------|-----
`git flow feature start MYFEATURE` | creates the feature branch
`git flow feature publish MYFEATURE` | share the feature branch
_your stuff_ | do some fancy work
`git commit -a -m "your final commit message"` | commit your stuff to local repository
`git flow feature pull origin MYFEATURE` | get latest for the public feature branch
`git flow feature finish MYFEATURE` | closes the branch
`git push origin develop` | Push the merged feature branch to remote
`git push origin :feature/MYFEATURE` | push the feature branch to remote



## Remember that your local repository must be initialized

command | comment
--------|-----
`git flow init` | initialize git-flow
`git remote add origin git@github.com:MYACCOUNT/MYREPO` | connect to the remote repository