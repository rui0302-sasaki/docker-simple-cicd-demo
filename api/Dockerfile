
FROM gradle:8-jdk17 AS build
WORKDIR /workspace
COPY . .

RUN gradle bootJar --no-daemon

FROM eclipse-temurin:17 AS production
WORKDIR /app
COPY --from=build /workspace/build/libs/*.jar ./api.jar
CMD [ "java", "-jar", "api.jar" ]