#stage -1  for volume mounting maven dependencies
FROM maven:3.6-jdk-11 AS build
COPY pom.xml .
RUN mvn -Dmaven.repo.local=$MVN_LOCAL_REPO dependency:go-offline
COPY src src
RUN mvn -Dmaven.repo.local=$MVN_LOCAL_REPO -f pom.xml clean package -DskipTests

#stage -2 for creating the image of the project
FROM openjdk:11
EXPOSE 8002
COPY --from=build /target/notes-0.0.1-SNAPSHOT.jar notes.jar
ENTRYPOINT ["java", "-jar", "/notes.jar"]
