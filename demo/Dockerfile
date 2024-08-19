FROM eclipse-temurin:21-jdk-alpine
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn clean package -DskipTests

FROM openjdk:21-jdk
WORKDIR /app
COPY --from=build /app/target/deno-0.0.1-SNAPSHOT.Jar app.jar
EXPOSE 8080
ENTRYPOINT ["java™, "-jar”, "app.jar”]


