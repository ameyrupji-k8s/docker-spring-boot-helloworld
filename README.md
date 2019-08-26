# docker-spring-boot-helloworld

Taking the Basic Hello World Application in Spring Boot! further. This example creates a docker container containing a Spring Boot application with a Controller that returns "Hello World!".


## Prerequisites

- Java IDE (I am using IntelliJ CE)
- Maven 


## System Configuration at time of test

- macOS Mojave - Version 10.14.6
- IntelliJ CE - Version CE 2019.2
- Maven - Version 3.6.1

## Initial Setup

### Creating Spring project

Follow the steps outlined in [spring-boot-helloworld](https://github.com/ameyrupji/spring-boot-helloworld) GitHub project to create a Spring Boot application.

### Dockerizing the application

Add `Dockerfile`

```
FROM openjdk:8-jre-alpine
COPY ./target/com.ameyrupji.helloworld-1.0-SNAPSHOT.jar /helloworld.jar

CMD ["/usr/bin/java", "-jar", "-Dspring.profiles.active=default", "/helloworld.jar"]

```

### Build docker image

To build the docker image run the following command on the terminal: `docker build -t spring-boot-helloworld:v1 .`

To list the created docker images run the command on the terminal: `docker images`


### Run the Docker Container

Run the following command to spin up the container server: `docker run -d -p 45678:9091 spring-boot-helloworld:v1`

To list all the containers running run this command on the terminal: `docker ps -a`


## Test 


Run the following command to ensure the server is running: `curl localhost:45678/helloworld/`

You can also view it in the browser by going to `http://localhost:45678/helloworld/` and following response will show up:

## Useful links

- https://github.com/ameyrupji/docker-nginx-static-html-demo
- https://stackify.com/guide-docker-java/

