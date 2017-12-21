## Spring Discovery Microservice


### Peace be upon you

---
#### Docker Part
Now, you should be able to build the Spring Config Microservice

Now, create the Dockerfile config file under your project directory and paste this:

```
FROM openjdk:8
VOLUME /tmp
ADD target/discovery-service-0.0.1-SNAPSHOT.jar app.jar
ENTRYPOINT ["java", "-jar", "app.jar"]
```
inside it.

Now open your terminal (for UNIX like users) or your command prompt (for windows users).

and copy paste this command:

```
docker build -f Dockerfile -t docker-spring-discovery .
```

Now all operations mentioned in the Dockerfile will be executed.

To test weather the image build was successful or not copy paste this command:

```
docker images
```
and you'll get a list of all available docker images on your computer.

Finally, you are ready to run the docker image with:
```
docker run -it -p 8888:8888 -e SPRING_CLOUD_CONFIG_SERVER_GIT_URI=https://github.com/mohamedmhiri/spring-microservices-config docker-spring-discovery
```
Move to the [next step](https://github.com/mohamedmhiri/docker-spring-microservices/tree/master/proxy-service).