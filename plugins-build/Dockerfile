# Use an official Maven image with JDK 8
FROM maven:3.8.8-eclipse-temurin-8 AS builder

# Set working directory inside the container
WORKDIR /app

# Clone the repository (Replace with your repository URL)
ARG REPO_URL
RUN git clone --depth 1 $REPO_URL src

# Change to source directory
WORKDIR /app/src

# Build the project with Maven
RUN mvn clean install -DskipTests


# Create a new minimal image with Java 8 JRE
FROM eclipse-temurin:8-jre

# Set working directory for the final image
WORKDIR /opt/app

# Define a volume for output JAR files
VOLUME /output

RUN mkdir -p /output-plugins

# Copy the built JARs from the previous stage
COPY --from=builder /app/src/plugins/filestorage/target/*.jar /output-plugins/
COPY --from=builder /app/src/plugins/lucene/target/*.jar /output-plugins/

# Set entrypoint
CMD ["sh", "-c", "cp -R /output-plugins/* /output/ && echo 'JARs copied to /output' && ls -lh /output"]
