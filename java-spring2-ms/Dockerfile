FROM gradle:9.3.1-jdk21-alpine
WORKDIR /app
COPY . .
RUN --mount=type=cache,target=/home/gradle/.gradle \
    --mount=type=cache,target=/app/build-cache \
    gradle bootJar

FROM eclipse-temurin:21.0.10_7-jre-alpine-3.23
WORKDIR /app
COPY --from=0 /app/applications/app-service/build/libs/JavaReactiveMS.jar /app/app-service.jar

ENV JAVA_OPTS="-XX:+UseContainerSupport"
ENTRYPOINT ["sh","-c","java $JAVA_OPTS -jar app-service.jar"]