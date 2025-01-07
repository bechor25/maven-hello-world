# Stage 1: Build stage
FROM maven:3.8.5-openjdk-11-slim AS builder
WORKDIR /app
COPY . .
RUN ls -R myapp

RUN mvn clean -f myapp/pom.xml package

# Stage 2: Runtime stage
FROM openjdk:11-jre-slim
WORKDIR /app
COPY --from=builder /app/myapp/target/maven-hello-world-*.jar app.jar
ENTRYPOINT ["java", "-jar", "app.jar"]