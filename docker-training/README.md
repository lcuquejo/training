# Useful docker commands

## To deploy a docker-compose stack
$ docker-compose up -d

## To stop the docker-compose stack
$ docker-compose stop

## To delete all containers from the docker-compose stack
$ docker-compose rm

## List all running containers
$ docker ps

## Lists of all existing containers (not only running)
$ docker ps -a

## How to access a running container
$ docker exec -it  {CONTAINER ID} /bin/bash

or

$ docker exec -it  {CONTAINER ID} /bin/sh

## Delete a container
$ docker rm {CONTAINER ID}

## Inspect a container
$ docker inspect {CONTAINER ID}

## List all downloaded images
$ docker images ls

## Delete image
$ docker rmi {IMAGE ID}

## List all networks
$ docker network ls

## Manually connect a container to a network
$ docker run --network test_default -it --name test  debian:latest /bin/bash

## Show all container  logs
$ docker logs  {CONTAINER ID}

## Show last lines 10 of log
$ docker logs --tail 10 -f  {CONTAINER ID}

# Docker Swarm (Cluster)
# Preparing the env
Make sure that you have a swarm cluster up.

```
$ docker node ls
```

Or create a new cluster by:
```
$ docker swarm init --default-addr-pool 172.66.66.0/16
```

Swarm official tutorial [https://docs.docker.com/engine/swarm/swarm-tutorial/deploy-service/]

## Show cluster nodes
$ docker node ls

## Create a new cluster
$ docker swarm init

## Generate manager | worker token
$ docker swarm join-token (worker|manager)

## Exit from a cluster
$ docker swarm leave

## Increase Service Replicas
$ docker service scale database_jump_sidecar=1

## Drain a node in swarm
$ docker node update --availability drain {NODE_ID}
## Back the note to active
docker node update --availability active  {NODE_ID}

## Show services
$ docker service ls

## Show where the service is running
$ dockser service ps {SERVICE ID}

## List stacks
$ docker stack ls

## Delete a stack
$ docker stack rm {STACK ID}

# CAUTION #
## Stop all running containers
$ docker stop $(docker ps -a -q)

## Delete all containers
$ docker rm $(docker ps -a -q)

# Fix the docker address-pool:
```
cat <<EOF | sudo tee /etc/docker/daemon.json
{
  "default-address-pools": [
    {
      "base": "172.66.66.0/16",
      "size": 24
    }
  ]
}
EOF

systemctl restart docker
```