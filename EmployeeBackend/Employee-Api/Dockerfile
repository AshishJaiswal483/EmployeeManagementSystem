
# Java 17 runtime and build environment
FROM maven:3.9.9-eclipse-temurin-17 AS build

WORKDIR /app

# Copy Maven project
COPY pom.xml .
COPY src ./src
COPY .mvn ./.mvn
COPY mvnw .

# Build Spring Boot application
RUN chmod +x mvnw && ./mvnw clean package -DskipTests

# Runtime image
FROM eclipse-temurin:17-jre

WORKDIR /app

COPY --from=build /app/target/Employee-Api-0.0.1-SNAPSHOT.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.jar"]
