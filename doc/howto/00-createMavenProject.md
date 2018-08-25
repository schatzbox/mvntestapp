# Creating a Maven Project


## Generating the Project

1. Create a directory 
`mkdir mvntestapp`
2. Generate a new project
`mvn archetype:generate -DgroupId=de.benjaminschatz.mvntestapp -DartifactId=mvntestapp -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false`

## Will create the following project structure

.
├── pom.xml
└── src
    ├── main
    │   └── java
    │       └── de
    │           └── benjaminschatz
    │               └── mvntestapp
    │                   └── App.java
    └── test
        └── java
            └── de
                └── benjaminschatz
                    └── mvntestapp
                        └── AppTest.java

## Building the Project

`mvn package`
 
## Will create the following stucture

.
├── pom.xml
├── src
│   ├── main
│   │   └── java
│   │       └── de
│   │           └── benjaminschatz
│   │               └── mvntestapp
│   │                   └── App.java
│   └── test
│       └── java
│           └── de
│               └── benjaminschatz
│                   └── mvntestapp
│                       └── AppTest.java
└── target
    ├── classes
    │   └── de
    │       └── benjaminschatz
    │           └── mvntestapp
    │               └── App.class
    ├── maven-archiver
    │   └── pom.properties
    ├── maven-status
    │   └── maven-compiler-plugin
    │       ├── compile
    │       │   └── default-compile
    │       │       ├── createdFiles.lst
    │       │       └── inputFiles.lst
    │       └── testCompile
    │           └── default-testCompile
    │               ├── createdFiles.lst
    │               └── inputFiles.lst
    ├── mvntestapp-1.0-SNAPSHOT.jar
    ├── surefire-reports
    │   ├── de.benjaminschatz.mvntestapp.AppTest.txt
    │   └── TEST-de.benjaminschatz.mvntestapp.AppTest.xml
    └── test-classes
        └── de
            └── benjaminschatz
                └── mvntestapp
                    └── AppTest.class

## Run the App

`java -cp target/mvntestapp-1.0-SNAPSHOT.jar de.benjaminschatz.mvntestapp.App`


## Clean the Project

`mvn clean`
