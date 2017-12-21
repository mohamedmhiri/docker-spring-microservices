## Docker Spring Microservices

### Peace be upon you

This project is a set of microservices developped with [Spring Boot](https://projects.spring.io/spring-boot/) and [Spring Cloud](https://projects.spring.io/spring-cloud/).

#### Spring Part

To build this application you can refer to this [Spring microservices tutorial](https://liliasfaxi.github.io/TP-eServices/tp4/) or you can just clone this project and use it.

---
#### Docker Part
Fist of all, install docker from the official [Docker](https://www.docker.com/) website.

Then, visite the [docker documentation](https://docs.docker.com/) to install docker and run the hello-world container to make sure that everything is ok.

You'll need also [docker-compose utility](https://docs.docker.com/compose/install/) to follow this tutorial.

You can now move to the [first microservice](https://github.com/mohamedmhiri/docker-spring-microservices/tree/master/config-service) and build it or move to the next step and use docker-compose instead.

Create the docker-compose config file under your project directory and paste this:

```
version: '2'
services:
  config-service:
    build:
        context: ./config-service
        dockerfile: Dockerfile
    ports:
     - 8888:8888
    networks:
     - spring-microservices-network

  product-service:
    build:
        context: ./product-service
        dockerfile: Dockerfile
    links:
     - config-service
    depends_on:
     - config-service
    ports:
     - 8080:8080
    networks:
     - spring-microservices-network
  
  discovery-service:
    build:
        context: ./discovery-service
        dockerfile: Dockerfile
    links:
     - config-service
    depends_on:
      - config-service
    ports:
     - 8761:8761
    networks:
     - spring-microservices-network

  proxy-service:
    build:
        context: ./proxy-service
        dockerfile: Dockerfile
    links:
     - config-service
     - discovery-service
    depends_on:
     - config-service
     - discovery-service
    networks:
     - spring-microservices-network
    ports:
     - 9999:9999


networks:
  spring-microservices-network:
      driver: bridge
```
inside it.

Now open your terminal (for UNIX like users) or your command prompt (for windows users).

and copy paste this command:

```
docker-compose build
```

Now all operations mentioned in the docker-compose will be executed.

And docker-spring-config, docker-spring-product, docker-spring-discovery and docker-spring-proxy images will be built.

To test weather if everything was successfully done or not copy paste this command:

```
docker images
```
and you'll get a list of all available docker images on your computer.

To finish this tutorial copy and paste the next line:
```
docker-compose up
```
Happy to help you.

