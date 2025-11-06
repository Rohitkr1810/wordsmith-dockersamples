FROM maven:3.8.3-eclipse-temurin-17 AS builder
WORKDIR /apps
COPY pom.xml .
COPY ./src ./src
RUN mvn clean package -DskipTests

FROM eclipse-temurin:21-jre
WORKDIR /apps
COPY --from=builder /apps/target/*.jar /apps/main.jar

EXPOSE 8080
ENTRYPOINT [ "java", "-jar", "/apps/main.jar" ]