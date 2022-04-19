# Build Stage
FROM maven:3.8.5-jdk-11-slim AS build
WORKDIR /home/app
COPY src .
COPY pom.xml .

RUN mvn -f /home/app/pom.xml clean package

# Package stage
FROM openjdk:11-jre-slim
COPY --from=build /home/app/target/demo-1.0.0.jar /usr/local/lib/demo-1.0.0.jar
CMD ["java", "-jar", "/usr/local/lib/demo-1.0.0.jar"]