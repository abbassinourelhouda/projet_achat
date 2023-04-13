# Étape de construction de l'application
FROM maven:3.8.3-openjdk-11-slim AS build
WORKDIR /app
COPY ../pom.xml .
COPY ../Achat_back/src/ ./src/
RUN mvn clean install -DskipTests

# Étape d'exécution de l'application
FROM openjdk:11-jdk-slim
COPY --from=build /app/target/tpAchatProject-1.0.jar /app.jar
EXPOSE 8089
CMD ["java", "-jar", "/app.jar"]