# SpringBoot-Docker

firs of all docker should be installed locally or on the target machine.

How to run spring boot app with docker?

1- using Docker file:
A file should be created with this name 'Dockerfile' in the project directory.

Docker file sample:

```
# Base image containing Java runtime.
FROM openjdk:17-jdk-slim

# maintainer of the image.
MAINTAINER  :developer <:email@gmail.com>

# add the application java to the container.
COPY target/user-service-0.0.1-SNAPSHOT.jar  user-service-0.0.1-SNAPSHOT.jar

# application execution
ENTRYPOINT ["java" , "-jar" , "/user-service-0.0.1-SNAPSHOT.jar"]
```





https://spring.io/blog/2020/01/27/creating-docker-images-with-spring-boot-2-3-0-m1


https://github.com/jonashackt/spring-boot-buildpack#spring-boot--cloud-native-build-packs
