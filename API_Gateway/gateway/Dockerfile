FROM maven:3.8.5-openjdk-17-slim AS gatewayBackendBuild
WORKDIR /root/src/backend
COPY . .
RUN mvn package  -DskipTests

FROM openjdk:17 AS gatewayBackendRuntime
WORKDIR /app
COPY --from=gatewayBackendBuild /root/src/backend/target/gateway-exe.jar ./
EXPOSE 8765
CMD java -jar gateway-exe.jar
