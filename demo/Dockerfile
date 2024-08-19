FROM eclipse-temurin:21-jdk-alpine as build
WORKDIR /app
COPY pom.xml .
RUN mvn dependency:go-offline -B

COPY src ./src
RUN mvn clean package -DskipTests

FROM eclipse-temurin:21-jdk-alpine
WORKDIR /app
COPY --from=build /app/target/demo-0.0.1-SNAPSHOT.Jar app.jar
EXPOSE 8080
ENTRYPOINT ["java™, "-jar”, "app.jar”]



