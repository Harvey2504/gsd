# Nodejs web app

Express app with handlebars view engine.

# Docker Installation 
Links : https://docs.docker.com/engine/install/

Note : Install using the convenience script for ubuntu systems.


# Added Commands

docker login (in terminal with username and password)

docker image build -t harvey2504/gsd:first-ctr .
```
(here harvey2504 is Docker Id)
(here gsd is Repo Name)
(here first-ctr is a tag)
```

docker image ls

docker image push harvey2504/gsd:first-ctr

docker image rm harvey2504/gsd:first-ctr
(deleting local image)

docker image ls

docker container run -d --name web -p 8000:8080 harvey2504/gsd:first-ctr

docker container ls

localhost:8000

docker container stop web (gracefully shut down)

docker container ls -a

docker container start web

(Stop and Delete)

docker container stop web

docker container rm web

docker container ls -a
(not a trace now)

(interactive thingie)

docker container -it --name test alpine sh
exit will kill the process and container too

ctrl+p+q graceful way to leave a container without burning it to ground

docker container rm test -f
(forcefully remove)



# Some more commands

Link : https://docs.docker.com/engine/reference/commandline/docker/


```
$ docker build .
(OR)
$ docker container commit c16378f943fe rhel-httpd:latest
(creates an image of the container)

$ docker tag <image id> harvey2504/gsd:f-ctr
(OR)
$ docker image tag rhel-httpd:latest registry-host:5000/myadmin/rhel-httpd:latest
(tags the image)

$ docker image push registry-host:5000/myadmin/rhel-httpd:latest
(push)
Remember to do a docker login once before pushing
```