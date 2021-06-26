# CREATE SIMPLE PROJECT WITH MAVEN

mvn archetype:generate -DgroupId=com.packt.cookbook -DartifactId=simple-project -DarchetypeArtifactId=mavenarchetype-quickstart -DinteractiveMode=false

# mvn package (build the project)
    - check if the sources are compiled
    - check if the test are run
    - jar file is now created

The package parameter is a phase in the build lifecycle
