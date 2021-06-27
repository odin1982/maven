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
