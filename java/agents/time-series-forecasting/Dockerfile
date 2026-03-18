FROM maven:3.8-openjdk-17@sha256:3a9c30b3af6278a8ae0007d3a3bf00fff80ec3ed7ae4eb9bfa1772853101549b AS builder

WORKDIR /app

COPY pom.xml .
RUN mvn dependency:go-offline -B

COPY src ./src

EXPOSE 8080

ENTRYPOINT ["mvn", "compile", "exec:java", \
    "-Dexec.args=--server.port=${PORT} \
    --adk.agents.source-dir=src/main/java \
    --logging.level.com.google.adk.dev=DEBUG \
    --logging.level.com.google.adk.demo.agents=DEBUG" \
    ]