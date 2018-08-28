# Creating Releases


command | comment
--------|-----
`git flow release start 1.0` | creates the release branch
_bump version in pom.xml_ | normally remove the -SNAPSHOT suffix
`git commit -a -m "version bumped to 1.0"` | commit the version bump
_your stuff_ | do some last minute work
`git commit -a -m "your final commit message"` | commit your stuff to local repository
_final check if the build succeeds_ | check if the version is OK
_do all the tests_ | you should only release without errors
`git flow release finish 1.0` | closes the branch
`git push origin master` | Push the merged release branch to remote master
`git push origin develop` | Push the merged release branch to remote develop
`git push origin --tags` | Don't forget to push the TAG
`git checkout develop` | be sure to be on **develop**
_bump version in pom.xml to the next planned release on **develop**_| normally increment subversion and add -SNAPSHOT suffix
`git commit -a -m "version bumped to 1.1-SNAPSHOT"` | commit the version bump
`git push origin develop` | Push the version bump remote develop




## Remember that your local repository must be initialized

command | comment
--------|-----
`git flow init` | initialize git-flow
`git remote add origin git@github.com:MYACCOUNT/MYREPO` | connect to the remote repository
