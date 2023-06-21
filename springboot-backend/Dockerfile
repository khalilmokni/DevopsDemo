# Use a base image with Java and Maven installed
FROM maven:3.8.4-openjdk-17 AS build

# Set the working directory
WORKDIR /app

# Copy the Maven project files to the container
COPY pom.xml .
COPY src ./src

# Build the application
RUN mvn clean package -DskipTests

# Create a new image for running the application
FROM openjdk:17-jdk-alpine

# Set the working directory
WORKDIR /app

# Copy the JAR file from the build stage
COPY --from=build /app/target/springboot-backend-0.0.1-SNAPSHOT.jar ./springboot-backend-0.0.1-SNAPSHOT.jar

# Expose the port on which the application will listen
EXPOSE 8080

# Run the application
CMD ["java", "-jar", "springboot-backend-0.0.1-SNAPSHOT.jar"]
