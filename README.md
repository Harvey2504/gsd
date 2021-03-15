# Getting Started with Docker

Official repo for Getting Started with Docker video training course by [@nigelpoulton](https://twitter.com/nigelpoulton)

## first-container

This folder contains the files to build a single-container web app (express, handlebars...)
- Docker hub image: [nigelpoulton/gsd:first-ctr](https://hub.docker.com/repository/docker/nigelpoulton/gsd)

## multi-container

NEEDS UPDATING
This folder contains the files to build a multi-container web app with Compose.
- Pthon flask app with redis cache
- Docker hub image: [nigelpoulton/gsd:compose-app](https://hub.docker.com/repository/docker/nigelpoulton/gsd)

## swarm-stack

This folder contains the files to build a multi-container web app with Swarm Stacks.
- Pthon flask app with redis cache that also returns hostname of container servicing request
- Docker hub image: [nigelpoulton/gsd:swarm-stack](https://hub.docker.com/repository/docker/nigelpoulton/gsd)


#Some Starting Blocks

https://www.youtube.com/watch?v=fqMOX6JJhGo
(Docker Tutorial) 



cat /etc/*release*
 sudo apt-get remove docker docker-engine docker.io containerd runc
 curl -fsSL https://get.docker.com -o get-docker.sh
 sudo sh get-docker.sh
 sudo docker version
 sudo docker run docker/whalesay cowsay boo

docker run :runs a container from image
docker ps :all running containers
docker ps -a :all containers
docker stop id/name
docker rm id/name :remove

docker images
docker rmi nginx
docker run nginx :starts a container
docker pull nginx : only downloads image

docker run ubuntu : will exit instantly
unlike vm
a container is not meant to host os . they just host a process or a specific task
a container lives as long as the process inside it is alive

docker run ubuntu sleep 5
docker exec nameofcontainer cat /etc/hosts

docker run kodekloud/simple-webapp
(attached mode)
docker run -d kodekloud/simple-webapp
(detached mode runs in background.Returns to promt immediately)
docker attach a043d (to return to attached mode)

docker image rm (id)
docker pull nginx:1.14-alpine
docker run --name webapp nginx:1.14-alpine

TAGS
docker run redis (default tag is latest)
docker run redis:4.0 (tags specified)

sudo docker run kodekloud/simple-prompt-docker
sudo docker run -i kodekloud/simple-prompt-docker
(Interactive mode with terminal)

PORT MAPPING/PORT PUBLISHING
docker run -d kodekloud/simple-webapp
The underlying host where docker is installed is called deocker host or docker engine
two ways
one to use the ip of docker container
every docker container gets an ip by default 
its an internal ip only accessible within host
so if we open a brrowser inside the docker put this ip:port
ex-http://172.17.0.2:5000
user outside of docker host cant access it 

We could use ip of docker host
for that to work you must map the port inside docker container to a free port on docker host
ex:
docker run -p 80:5000 kodekloud/simple-webapp
docker run -p 8306:3306 mysql
docker run -p 8305:3306 mysql
docker run -p 8305:3306 mysql xcant map again to 8305

VOLUME MAPPING for persisten data

docker run -v /opt/datadir:/var/lib/mysql mysql
so data will be persistent int opt/datadir even if we stop and delete the container
Check through
docker volume ls
docker volume inspect volume_name (docker volume inspect todo-db)

docker ps (basic info)
docker inspect id/name
it returns all details of container in json format
It also shows us the networking info and ip and type.

Logs of containers
docker logs name/id

Env Variables
docker run -e APP_COLOR=blue simple-webapp-color
know what all env variables present through docker inspect name/id

how to create my own image?
Dockerfile
FROM Ubuntu (base OS/another image)
RUN apt-get update (install all dependencies)
RUN apt-get install python
RUN pip install flask
RUN pip install flask-mysql
COPY ./opt/source-code (copy source code)
ENTRYPOINT FLASK_APP=/opt/source-code/app.py flask run
(specify entry point whwn image is run as an container)

All are built in layered architecture as per instruction

(creates an image locally on system)
docker build Dockerfile -t atib/myapp
(creates an image on docker registry)
docker push atib/myapp

Dockerfile
INSTRUCTION  --- argument format
(caps)       --- 

docker history imagename
to see how many memory each layer takes up

all the layers build are cached.so you havent to start from all over again if u run again with some additions
so rebuilding an image is faster


incase of cmd command the commandline args override it but in case of entrypoint they just append to it.
Refer Screenshots.















Ref Links:
https://docs.docker.com/
http://hub.docker.com/


