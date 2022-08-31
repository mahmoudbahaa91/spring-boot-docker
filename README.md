# SpringBoot-Docker

first of all, docker should be installed locally or on the target machine.

## How to build spring boot app with docker?

###### 1- using Docker file:

a file should be created with this name 'Dockerfile' in the project directory.

Dockerfile sample:

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
Maven configuration sample

```
	<build>
		<plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
				<configuration>
					<image>
						<name>${project.artifactId}-image</name>
					</image>
				</configuration>
			</plugin>
		</plugins>
	</build>
```

###### 2- using buildpacks:

 buildpack is a set of executables that inspects your app source code and creates a plan to build and run your application,
 so the docker image will be created automatically from source code wihout the need to create a Dockerfile
 
 Command:
 mvn spring-boot:build-image


--------------------------------------------------------------------------------------------------------------------------------

## How to run spring boot app with docker?

1- in case of Docker file, we should build the image first

// building an image (. means same folder, -t means a tag)
docker build . -t user-service-image        

// run 
docker run -p  8080:8080 user-service-image


2- in case of Buildpacks: 

// run 
docker run -p  8080:8080 user-service-image



