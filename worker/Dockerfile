# Build stage

FROM maven AS builder

WORKDIR /app

COPY . .

RUN mvn clean package -DskipTests

# Final stage

FROM chainguard/jre

WORKDIR /app

COPY --from=builder /app/target/worker-*.jar ./worker.jar

ENTRYPOINT ["java", "-jar", "worker.jar"]