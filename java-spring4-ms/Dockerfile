FROM gradle:9.3.1-jdk25-alpine
WORKDIR /app
COPY . .
RUN gradle bootJar

FROM eclipse-temurin:25.0.2_10-jre-alpine-3.23
WORKDIR /app
COPY --from=0 /app/build/libs/spring-0.0.1-SNAPSHOT.jar /app/spring-0.0.1-SNAPSHOT.jar

ENV JAVA_OPTS="-XX:+UseContainerSupport"
ENTRYPOINT ["sh","-c","java $JAVA_OPTS -jar spring-0.0.1-SNAPSHOT.jar"]