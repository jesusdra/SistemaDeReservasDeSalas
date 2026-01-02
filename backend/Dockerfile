FROM ubuntu:latest AS build

RUN apt-get update
RUN apt-get install	openjdk:21-jdk-alpine -y
COPY . .

RUN apt-get install maven -y
RUN mvn clean install

FROM openjdk:21-jdk-alpine
EXPOSE 8080

COPY --from=build /target/*.jar app.jar

ENTRYPOINT [ "java", "-jar", "app.jar" ]
