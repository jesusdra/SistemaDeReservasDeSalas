FROM ubuntu:latest AS build

RUN apt-get update
RUN apt-get install	openjdk:27-jdk -y
COPY . .

RUN apt-get install maven -y
RUN mvn clean install

FROM openjdk:27-jdk
EXPOSE 8080

COPY --from=build /target/*.jar app.jar

ENTRYPOINT [ "java", "-jar", "app.jar" ]
