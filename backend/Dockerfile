# ── Stage 1 : build (Compile le code) ─────────────────────────────────
FROM maven:3.9.6-eclipse-temurin-21-alpine AS build
WORKDIR /app

# Cache les dépendances Maven
COPY pom.xml .
RUN mvn dependency:go-offline -q

# Compile le JAR
COPY src ./src
RUN mvn clean package -DskipTests -q

# ── Stage 2 : run (Exécute l'application) ──────────────────────────────
FROM eclipse-temurin:21-jre-alpine
WORKDIR /app

# Sécurité : Création d'un utilisateur non-root
RUN addgroup -S LTS && adduser -S LTS -G LTS
USER LTS

# Récupère uniquement le JAR du stage précédent
COPY --from=build /app/target/*.jar app.jar

EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]