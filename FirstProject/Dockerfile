FROM java:8 
FROM maven:3.5.2-jdk-8-alpine AS MAVEN
COPY pom.xml /tmp/
COPY src /tmp/src/
WORKDIR /tmp/
RUN mvn package
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "target/FirstProject-1.0-SNAPSHOT.jar"]