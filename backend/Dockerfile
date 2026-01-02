FROM ubuntu:latest AS build

RUN apt-get update
RUN apt-get install openjdk-21-slim-bullseye -y
COPY . .

RUN apt-get install maven -y
RUN mvn clean install

FROM openjdk:21-jdk-slim-bullseye
EXPOSE 8080

COPY --from=build /target/*.jar app.jar

ENTRYPOINT [ "java", "-jar", "app.jar" ]
