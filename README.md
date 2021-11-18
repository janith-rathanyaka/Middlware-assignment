# PetStore Application

#Prerequisite Installation.
1) Java Version 11.0 or above
2) Docker Desktop
3) Docker Compose
4) SQL Database (PostgreSQL)
5) use https://github.com/janith-rathanyaka/Middlware-assignment

#Downloading the Application

1) https://github.com/janith-rathanyaka/Middlware-assignment


## Database Connection Implementation
change petstore\src\main\resources\application.properties 
   quarkus.datasource.password=1234  -- change password
   quarkus.datasource.jdbc.url=jdbc:postgresql://localhost:5432/petstore -- database name

## Running the application in dev mode

You can run your application in dev mode that enables live coding using:

    ./gradlew quarkusDev

> **_NOTE:_**  Quarkus now ships with a Dev UI, which is available in dev mode only at http://localhost:8080/q/dev/.

## Creating a native executable

Mind having GRAALVM_HOME set to your Mandrel or GraalVM installation.

You can create a native executable using:

    ./gradlew build -Dquarkus.package.type=native

Or, if you don't have [Mandrel](https://github.com/graalvm/mandrel/releases/) or
[GraalVM](https://github.com/graalvm/graalvm-ce-builds/releases) installed, you can run the native executable
build in a container using:

    ./gradlew build -Dquarkus.package.type=native -Dquarkus.native.container-build=true

Or to use Mandrel distribution:

    ./gradlew build -Dquarkus.package.type=native -Dquarkus.native.container-build=true -Dquarkus.native.builder-image=quay.io/quarkus/ubi-quarkus-mandrel:20.3-java11

You can then execute your native executable with:

    ./build/petstore-runner
    
##   Deploying Application
start Docker compose after this use this command steps:
1) ./gradlew build
2) docker build -f src/main/docker/Dockerfile.jvm -t quarkus/code-with-quarkus-jvm .
3) docker run -i --rm -p 8080:8080 quarkus/code-with-quarkus-jvm


