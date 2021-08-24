# Spring Boot microservice deployed in docker

A Spring Boot project running inside a docker container.

## Running the project inside a container

### Using docker commands:

We can run docker from the target folder after mvn install with the following command:

```
docker run -p 3000:8080 -v $(pwd):/var/www -w "/var/www" openjdk:8 java -jar spring-petclinic-2.4.5.jar
```

### Using docker file:

But a better option will be with a docker file. I have added 2 docker files for this project:

#### Dockerfile

This file builds and starts the spring boot application all inside the container.

To build the image execute the following command:

```
docker build --tag java-docker .
```

And to run the container:

```
docker run -p 3000:8080 java-docker
```

I also have included the __.dockerignore__ file which has a similar purpose as the _.gitignore_ file.

More information about this configuration [here](https://docs.docker.com/language/java/build-images/).

#### DockerfileJar

In order to create the image for the project:

```
docker build -f DockerfileJar -t wayqui/spring-petclinic .
```

And if we want to generate a container for that image and run it:

```
docker run -d -p 3000:8080 wayqui/spring-petclinic
```

### Publishing the image into docker hub:

```
docker push wayqui/docker-demo
```

## Communicate between containers


