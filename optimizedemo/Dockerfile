FROM maven:3.9.6-eclipse-temurin-21-alpine AS BUILD
COPY . .
RUN mvn clean install

FROM openjdk:17.0.2-jdk-slim as RUN

COPY --from=BUILD target/optimizedemo-*.jar optimize-demo.jar

RUN apt-get update && apt-get install -y curl

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "optimize-demo.jar"]