FROM eclipse-temurin:17 AS build
WORKDIR /workspace
COPY . .
RUN ./gradlew bootJar

FROM eclipse-temurin:17 AS production
COPY --from=build /workspace/build/libs/api-0.0.1-SNAPSHOT.jar ./api.jar
CMD [ "java", "-jar", "api.jar" ]
