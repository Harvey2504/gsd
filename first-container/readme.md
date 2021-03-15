# Nodejs web app

Express app with handlebars view engine.


#Added
docker login (in terminal with username and password)

docker image build -t harvey2504/gsd:first-ctr .
(here harvey2504 is Docker Id)
(here gsd is Repo Name)
(here first-ctr is a tag)

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



