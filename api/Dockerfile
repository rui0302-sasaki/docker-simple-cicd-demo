FROM eclipse-temurin:17 AS build
WORKDIR /workspace

COPY . .
RUN apt-get update && apt-get install -y findutils
RUN ./gradlew bootJar || gradle bootJar

FROM eclipse-temurin:17 AS production
COPY --from=build /workspace/build/libs/*.jar ./api.jar
CMD [ "java", "-jar", "api.jar" ]