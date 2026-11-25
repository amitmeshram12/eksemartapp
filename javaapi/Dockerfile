
FROM eclipse-temurin:8-jdk AS BUILD_IMAGE

WORKDIR /usr/src/app/

RUN apt-get update && apt-get install -y maven \
    && rm -rf /var/lib/apt/lists/*

COPY ./ /usr/src/app/

RUN mvn clean install -DskipTests

FROM eclipse-temurin:8-jre

WORKDIR /usr/src/app/

COPY --from=BUILD_IMAGE /usr/src/app/target/book-work-0.0.1-SNAPSHOT.jar ./book-work-0.0.1.jar

EXPOSE 9000

ENTRYPOINT ["java", "-jar", "book-work-0.0.1.jar"]
