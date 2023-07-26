FROM maven:3.8.5-jdk-11 as builder
# WORKDIR /src/main/java/com/example/cloudsql
COPY pom.xml .
RUN mvn -B dependency:resolve
COPY src ./src
RUN mvn -B package

FROM openjdk:11-jdk-slim
# WORKDIR /src/main/java/com/example/cloudsql
COPY --from=builder target/demo-1.0-SNAPSHOT.jar demo-1.0-SNAPSHOT.jar
EXPOSE 8080
CMD ["java", "-cp", "demo-1.0-SNAPSHOT.jar", "hello.App"]