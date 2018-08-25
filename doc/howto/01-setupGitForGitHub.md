# Setup Git

`git config --global user.name NAME`

`git config --global user.email EMAIL@ADRESSE.de`

`git config --global color.ui "auto"`

`git config --global pack.threads "0"`

`git init`

    Leeres Git-Repository in /home/benny/git-repos/mvntestapp/.git/ initialisiert

`git add -A`


# Create Readme

`echo "# Hello World" >README.md`

`git add README.md`


# View Git status

`git status`

    Auf Branch master
    
    Noch keine Commits
    zum Commit vorgemerkte Änderungen:
    (benutzen Sie "git rm --cached <Datei>..." zum Entfernen aus der Staging-Area)
    
    neue Datei:     README.md
    neue Datei:     doc/createMavenApp.txt
    neue Datei:     pom.xml
    neue Datei:     src/main/java/de/benjaminschatz/mvntestapp/App.java
    neue Datei:     src/test/java/de/benjaminschatz/mvntestapp/AppTest.java


# Create GitHub Account

on [GitHub](https://github.com)


# Create Repository on GitHub

Notice that the name should be the same as the repository's on the local system

> mvntestapp


# Committing change

`git commit -m "my first commit"`

    [master (Basis-Commit) 4529afe] my first commit
    5 files changed, 165 insertions(+)
    create mode 100644 README.md
    create mode 100644 doc/createMavenApp.txt
    create mode 100644 pom.xml
    create mode 100644 src/main/java/de/benjaminschatz/mvntestapp/App.java
    create mode 100644 src/test/java/de/benjaminschatz/mvntestapp/AppTest.java


# Connecting the GitHub repository

`git remote add origin https://github.com/schatzbox/mvntestapp.git`


# Pushing the files to GitHub

`git push -ff origin master`


    Username for 'https://github.com': schatzbox 
    Password for 'https://schatzbox@github.com': 
    Zähle Objekte: 19, Fertig.
    Delta compression using up to 2 threads.
    Komprimiere Objekte: 100% (7/7), Fertig.
    Schreibe Objekte: 100% (19/19), 2.25 KiB | 577.00 KiB/s, Fertig.
    Total 19 (delta 0), reused 0 (delta 0)
    To https://github.com/schatzbox/mvntestapp.git
     + 1af7bc7...4529afe master -> master (forced update)
