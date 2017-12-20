FROM openjdk:8
VOLUME /tmp
ADD target/config-service-0.0.1-SNAPSHOT.jar app.jar
ENTRYPOINT ["java", "-jar", "app.jar"]