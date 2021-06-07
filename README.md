# Dockerizing the Azkaban 4.0 version

Deploy Azkaban Executor as Docker Container

## Getting Started

This is the docker image for the Azkaban Executor

### Prerequisites

Has docker installed on your machine, If you're using Mac, Use this link for Docker Setup - https://docs.docker.com/docker-for-mac/install/

#### Database Setup
Follow the steps to create user, grant permissions and also setup entire DB

Creating Azkaban user with default credentials by logging into MySQL Console, Run the following commands.

```
mysql> create user 'azkaban'@'%' identified by 'azkaban';
```

Once the user is created, Create a database name `azkaban`

```
mysql> create database azkaban;
```

Grant permissions to `azkaban` user for `azkaban` DB

```
mysql> grant all privileges on azkaban.* to 'azkaban'@'%';
```

Once this is done, Let us create all the schema required for Azkaban.

```
$ mysql -uazkaban -pazkaban azkaban < <Project-Path>/azkaban-4.0.0/azkaban-db/build/sql/create-all-sql-0.1.0-SNAPSHOT.sql
```


#### Multi Executor

Follow the steps to make it working in your Mac 

```
$ docker network create azk-net
```
This creates bridge network in your local

```
$ docker run --env AZK_MYSQL_HOST=host.docker.internal --network azk-net -d --rm -p 80:8081 anandimmannavar/azkaban-exec:2.0
```
Here we are running executor container and connecting it to the bridge network created `azk-net`


```
$ docker run --env AZK_MYSQL_HOST=host.docker.internal --network azk-net -d --rm -p 80:8081 anandimmannavar/azkaban-web:2.0
```
Running Azkaban Web Server and also connect this web server to `azk-net` bridge network
