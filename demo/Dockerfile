FROM eclipse-temurin:21-jdk-alpine

WORKDIR /app

RUN ./mvnw clean install -DskipTests

COPY . .

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.jar"]
