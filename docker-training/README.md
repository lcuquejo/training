Useful docker commands

To deploy a docker-compose stack
$ docker-compose up -d
or
$ docker stack deploy -c docker-compose.yml  myStack

To stop the docker-compose stack
$ docker-compose stop

To delete all containers from the docker-compose stack
$ docker-compose rm

List all running containers
$ docker ps

Lists of all existing containers (not only running)
$ docker ps -a

How to access a running container
$ docker exec -it  {CONTAINER ID} /bin/bash
or 
$ docker exec -it  {CONTAINER ID} /bin/sh 

Delete a container
$ docker rm {CONTAINER ID}

Inspect a container
$ docker inspect {CONTAINER ID}

List all downloaded images
$ docker images ls

Delete image
$ docker rmi {IMAGE ID}

List all networks
$ docker network ls

Manually connect a container to a network
$ docker run --network test_default -it --name test  debian:latest /bin/bash

Show all container  logs
$ docker logs  {CONTAINER ID}

Show last lines 10 of log 
$ docker logs --tail 10 -f  {CONTAINER ID}

### CAUTION ###
Stop all running containers
$ docker stop $(docker ps -a -q)

Delete all containers
$ docker rm $(docker ps -a -q)