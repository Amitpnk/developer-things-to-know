# Docker
 
Docker commands

## Table of Contents

- [Sending Feedback](#sending-feedback)
- [About Docker](#about-entity-framework-core)
- [Installing docker](#sample-application-with-each-steps)
    - [Desktop for windows](#desktop-for-windows)
    - [Visual studio extension](#visual-studio-extension)
    - [Check status/info of docker](#check-statusinfo-of-docker)
- [Running container locally](#running-container-locally)
    - [Docker run](#docker-run)
    - [List containers](#docker-run)
    - [Docker logs](#docker-run)
    - [Docker run](#docker-run)
    - [Docker images downloaded](#docker-images-downloaded)
    - [Docker Exec](#docker-Exec])
    - [Storing container data](#storing-container-data)
    - [Summary](#summary])

## About docker


## Installing Docker

### Desktop for windows

[Install Docker Desktop for Windows](https://docs.docker.com/docker-for-windows/install/)

### Visual studio extension

[VS Market place](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker)

[VS code extension](https://code.visualstudio.com/docs/containers/overview)

### Check status/info of docker

```sh
docker version
docker info
docker --help
```

## Running container locally

Example of running redis container locally 

### Docker run 

Download from image and running redis image locally

```sh
docker run -d -p 6379:6379 --name redis1 redis
```

### List containers

To check status of container list availabe locally

```sh
docker ps
```

### Docker logs

Logs output

```sh
docker logs redis1
```

### Docker images downloaded

List of all docker images downloaded

```ps
docker image ls
```

### Docker Exec

running inside redis container

```ps
docker exec -it redis1 sh
# redis-cli
120.0.0.1:6379> ping
PONG
120.0.0.1:6379> set name amit
OK
120.0.0.1:6379> get name
"amit"
120.0.0.1:6379> incr counter
(interger) 1
120.0.0.1:6379> incr counter
(interger) 2
120.0.0.1:6379> get counter
"2"
120.0.0.1:6379> exit
# exit
```

running redis with different container and attaching to first container

```ps
docker run -it --rm --link redis1:redis --name client1 redis sh
# redis-cli -h redis
redis:6379> get name
"amit"
redis:6379> get counter
"2"
redis:6379> exit
# exit
```

list of containers

```sh
docker ps
```

stopping container

```sh
docker stop redis1
```

now redis container will not shown

```sh
docker ps
```

to display redis container inactive status

```sh
docker ps -a
```

to remove container, but only images will remanin

```sh
docker rm redis1
```

to see docker images

```ps
docker image ls
```

to delete images

```ps
docker image rm redis
```

### Storing container data

```ps
docker run -d -p 5432:5432 -v postgres-data:/var/lib/postgresql/data --name postgres1 postgres -e POSTGRES_PASSWORD=password
```

run in container 

```ps
docker exec -it postgres1 sh
# createdb -U postgres mydb
# psql -U postgres mydb
psql (10.5 (Debian 10.5-1.pgdg90+1))
Type "help" for help.

mydb=# CREATE TABLE people (id int, name varch(50));
CREATE TABLE
mydb=# INSERT INTO people (id, name) VALUES (1, 'AMIT');
INSERT 0 1
mydb=# \Q
# exit
```

force stop /delete container

```ps
docker rm -f postgres1
```

list of volumes

```ps
docker volume ls
```

create another container with differenet container name as postgres2

```ps
docker run -d -p 5432:5432 -v postgres-data:/var/lib/postgresql/data --name postgres2 postgres -e POSTGRES_PASSWORD=password
```

run in container 

```ps
docker exec -it postgres2 sh
# psql -U postgres mydb
psql (10.5 (Debian 10.5-1.pgdg90+1))
Type "help" for help.

mydb=# SELECT * FROM people;
id  |   name
----+-------
 1  |   amit

mydb=# \q
# exit
```

force stop /delete container

```ps
docker rm -f postgres2
```

delete volume

```ps
docker volume rm postgres-data
```

### Summary

* docker run 
    * -d (run detached)
    * -it (interactive terminal)
    * -p (publish a port)
    * -v (mount a volume)
    * --name (name of container)
    * --link (communicate between containers)
    * --rm (auto delete when container stops)
    * -e NAME=value (environment variables)
* docker exec
    * run command inside a container
* docker ps
    * see what containers are running
* docker logs
    * view log output from container
* clean up
    * docker rm -f container-name
    * docker image rm image-name
    * docker volume rm volume-name    

## Reference

[docker cli docs](https://docs.docker.com/engine/reference/commandline/images/)