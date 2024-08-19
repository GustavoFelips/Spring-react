# Etapa 1: Construir a aplicação
FROM eclipse-temurin:21-jdk-alpine as build
WORKDIR /app

# Instale o Maven
RUN apk add --no-cache maven

# Copie o arquivo pom.xml e baixe as dependências do Maven
COPY pom.xml ./
RUN mvn dependency:go-offline -B

# Copie o código-fonte e execute o build da aplicação
COPY src ./src
RUN mvn clean package -DskipTests

# Etapa 2: Criar a imagem final com o JAR empacotado
FROM eclipse-temurin:21-jdk-alpine
WORKDIR /app

# Copie o JAR do estágio de build
COPY --from=build /app/target/deno-0.0.1-SNAPSHOT.jar app.jar

# Exponha a porta 8080
EXPOSE 8080

# Defina o comando de inicialização da aplicação
ENTRYPOINT ["java", "-jar", "app.jar"]
