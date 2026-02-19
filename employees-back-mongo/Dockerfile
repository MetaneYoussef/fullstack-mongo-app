### STAGE 1: Build ###
FROM openjdk:11.0.11-slim-buster as build                         
RUN mkdir -p /app
WORKDIR /app
 
COPY .mvn/ .mvn
COPY mvnw pom.xml .
COPY src ./src 

RUN chmod +x mvnw
RUN ./mvnw -B package  


### STAGE 2: RUN ###

FROM openjdk:14-ea-8-jdk-alpine3.10

COPY --from=build /app/target/*.jar app.jar

ENTRYPOINT ["java","-jar", "/app.jar"]
