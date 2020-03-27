#Build
FROM maven:3-jdk-8 AS build
COPY src /healthcheck/src
COPY pom.xml /healthcheck
RUN mvn -f /healthcheck/pom.xml clean package

#Run
FROM openjdk:8-jre
COPY --from=build /healthcheck/target/healthcheck-0.0.1-SNAPSHOT.jar /healthcheck.jar
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/healthcheck.jar"]