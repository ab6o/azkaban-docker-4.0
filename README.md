# Dockerizing the Azkaban 4.0 version

Deploy Azkaban Executor as Docker Container

## Getting Started

This is the docker image for the Azkaban Executor

### Prerequisites

Has docker installed on your machine, If you're using Mac, Use this link for Docker Setup - https://docs.docker.com/docker-for-mac/install/


#### Multi Executor

Follow the steps to make it working in your Mac 

```
$ docker network create azk-net
```
This creates bridge network in your local

```
$ docker run --env AZK_MYSQL_HOST=host.docker.internal --network azk-net -d --rm -p 80:8081 anandimmannavar/azkaban-exec:1.0
```
Here we are running executor container and connecting it to the bridge network created `azk-net`
