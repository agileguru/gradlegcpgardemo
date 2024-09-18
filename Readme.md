# Example Repo For Gradle custom properties for Google Artifact Registry

This is a sample repository to integrate Google Artifact Registry and Gradle for developer and CI system to avoid slow buils and cost optomization by reducing egress and ingress costs from Google Artifact Registry. The Idea is to use direct connection to public maven repo for developers as much as possible and use internal URL for CI systems. 

## Use Case 

1. Developers need access to internal artefacts if needed but access external artefacts from https://repo1.maven.org/maven2 to avoid INGRESS EGRESS charge from GCP
1. CI system needs to access internal artefacts if needed but access external artefacts from artifactregistry://us-central1-maven.pkg.dev/<project-id>/<external-repo-name>/


### How To implement for Developer

1. Copy developer.gradle.properties to the GRADLE_USER_HOME ( normally .gradle in use home directory )
1. Use the properties defined as repository values in this file in your build.gradle


### How To implement for CI

1. Copy ci.gradle.properties to the GRADLE_USER_HOME ( normally .gradle in use home directory )
1. Use the properties defined as repository values in this file in your build.gradle


## WARNING 

Make sure that both the files have same properties (key) but different values as appropriate


## Test and expected Outcome 

1. Copy / Mount the apporopriate properties file as gradle.properties in GRADLE_USER_HOME
1. Build the application using ./gradlew  build as normal or ./gradlew  build --i for showing the download URL



## The settings.gradle 

1. In  settings.gradle you  have the default plugin url set to pluginurl from the properties file . This is https://plugins.gradle.org/m2/  