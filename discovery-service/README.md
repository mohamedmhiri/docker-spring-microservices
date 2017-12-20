## Spring Discovery Microservice


### Peace be upon you

---
#### Docker Part
Fist of all, install docker from the official [Docker](https://www.docker.com/) website.

Then, visite the [docker documentation](https://docs.docker.com/) to install docker and run the hello-world container to make sure that everything is ok.

Now, create the Dockerfile config file under your project directory and paste this:

```
FROM openjdk:8
ADD target/discovery-service-0.0.1-SNAPSHOT.jar app.jar
EXPOSE 8761
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

Now, you are ready to run the docker image with:
```
docker run -it -p 8761:8761 docker-spring-discovery
```
