# CREATE SIMPLE PROJECT WITH MAVEN

mvn archetype:generate -DgroupId=com.packt.cookbook -DartifactId=simple-project -DarchetypeArtifactId=mavenarchetype-quickstart -DinteractiveMode=false

# mvn package (build the project)
    - check if the sources are compiled
    - check if the test are run
    - jar file is now created

The package parameter is a phase in the build lifecycle

# DIRECTORIES MAVEN

Now let's briefly discuss what these directories contain:

- The BIN folder contains the batch files and shell scripts to run Maven on various platforms.
- The BOOT folder contains the jars required for Maven to start.
- The CONF folder contains the default settings.xml file used by Maven.
- The LIB folder contains the libraries used by Maven. It also contains an ext folder in which    third-party extensions, which can extend or override the default Maven implementation, can be placed.

# MAVEN REPOSITORIES

There are three types of Maven repositories:
- LOCAL:    This is the repository in your computer filesystem.
- REMOTE:   This is the repository from where the required Maven files get downloaded.
- MIRRORS:  These are repository managers, such as Nexus and Artifactory, that mirror
various repositories.

# HOW TO CHANGE .M2 UBICATION

1. Create a file called settings.xml in the .m2 folder.
2. Add the following contents to the settings.xml file that you just created:
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0
 http://maven.apache.org/xsd/settings1.0.0.xsd">
 <localRepository>C:/software/maven</localRepository>
</settings>
Notice the highlighted part of the preceding code. We have changed the location of
the repository contents to C:\software\maven. You can change it to any valid folder
name.
3. Delete the repository subfolder and run the mvn package command again.
You will now notice that the repository folder is not created in the .m2 folder.
Instead, it is created in C:\software\maven

# MAVEN LIFECYCLE

While each lifecycle has a number of phases, let us look at the important phases for each lifecycle:
- The clean lifecycle: The clean phase removes all the files and folders created by Maven as part of its build
- The site lifecycle: The site phase generates the project's documentation, which can be published, as well as a template that can be customized further
- The default lifecycle: The following are some of the important phases of the default lifecycle:
    - validate: This phase validates that all project information is available and correct
    - process-resources: This phase copies project resources to the destination to package
    - compile: This phase compiles the source code
    - test: This phase runs unit tests within a suitable framework
    - package: This phase packages the compiled code in its distribution format
    - integration-test: This phase processes the package in the integration test environment
    - verify: This phase runs checks to verify that the package is valid
    - install: This phase installs the package in the local repository
    - deploy: This phase installs the final package in the configured repository

# POM (Project Object Model)

## SCHEMA

```
<project    xmlns="http://maven.apache.org/POM/4.0.0"
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
            xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
```
## VERSION SCHEMA

```
<modelVersion>4.0.0</modelVersion>
```

## GROUPID

The groupId element is a unique identifier of the organization to which the project belongs.
For our sample project, it is org.packt.cookbook. It is a good practice to follow the reverse
domain name notation to specify this:

```
<groupId>...</groupId>
```

## ARTIFACT ID
The artifactId element is the name of the project

```
<artifactId>...</artifactId>
```

## VERSION
The version element is the specific instance of the project, corresponding to the source
code at a particular instance of time.

```
<version>...</version>
```

## PACKAGING

The packaging element indicates the artifact type of the project. This is typically a jar, war, zip, or in some cases, a pom:

```
<packaging>...</packaging>
```

## DEPENDECNIES
The dependencies element section of the pom file defines all the dependent projects of this project. This would typically be third-party libraries required to build, test, and run the project:

```
<dependencies>...</dependencies>
```

## PARENT
The parent section is used to indicate a relationship, specifically a parent-child relationship. If the project is part of a multi-module project or inherits project information from another project, then the details are specified in this section:

```
<parent>...</parent>
```

## PROPERTIES
Maven properties are placeholders. Their values are accessible anywhere in the pom file by using ${key}, where key is the property name:

```
<properties>...</properties>
```

## MODULES
A project with modules is known as a multi-module or aggregator project. Modules are projects that this pom file lists and are executed as a group:

```
<modules>...</modules>
```

## COMMAND LINE OPTION IN MAVEN
$ mvn -h            --> Options that Maven supports

-e -errors          --> When there is an error, this flag display the  details of errors
-q -quiet           --> Only errors are displayed
-v -version         --> Only show if Maven is installed and Maven version
-o -offline         --> Maven doesn't not attempt to download any dependency or plugin from the internet
-X -debug           --> Maven prints a lot of verbose output

## PROFILE ELEMENTS
<profile>
    <id>test</id>
    <activation>...</activation>
    <build>...</build>
    <modules>...</modules>
    <repositories>...</repositories>
    <pluginRepositories>...</pluginRepositories>
    <dependencies>...</dependencies>
    <reporting>...</reporting>
    <dependencyManagement>...</dependencyManagement>
    <distributionManagement>...</distributionManagement>
</profile>

## Activating/deactivating a Maven profile
    <activeByDefault>false</activeByDefault>

## command to check if the profile is active
    $ mvn help:active-profiles

## Invoke a profile coomand line
    $ mvn –P dev package

## Skipping the compilation of test sources
    $ mvn –Dmaven.test.skip=true package

## Revisar la lista de las dependencia de tu proyecto
    $ mvn dependency:list

## Revisar una forma mas detallada de la lista de dependencias de tu proyecto
    $ mvn dependency:tree