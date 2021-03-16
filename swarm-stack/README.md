# Swarm stack

Python flask app:
- stores counter in redis
- returns count and hostname of contriner servicing request


#Additions\\

stack on a swarm do not support building images on the fly
webfrontend image must be pre created here

docker image build -t harvey2504/gsd:swarm_stack .

docker image push harvey2504/gsd:swarm_stack

docker stack deploy -c docker-compose.yml counter

docker stack ls

docker stack services counter

docker stack ps counter

localhost:5000 visit

open yml file and make desired changes from there only.
(upscaling/downscaling)
(like edit replica to 5)
(this way it remains the source of truth for dev and ops)

docker stack deploy -c docker-compose.yml counter

docker stack ps counter

docker stack rm counter


docker swarm init
docker swarm leave -f



