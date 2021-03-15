# Simple counter-app for demonstrating Docker Compose
Simple flask app that counts web site visits and stores in a default Redis backend.

**References:**
- Getting Started with Docker video training course


#Docker Swarm Additional

docker swarm init b(if on docker desktop)

docker swarm init --advertise-addr=192.168.0.20

(add worker or swarm accordingly with the token)
(run those tokens in all host nodes u want to assign)
(try to have odd number of manager (1leader+followers))

docker node ls

with swarm up and running . Two features gets unlocked
services object and stack command

docker service create --name web -p 8080:8080 --replicas 3 harvey2504/gsd:firstcontainer
(service replica is a container)

docker service ls 

docker container ls (side door peeking) (shows only what is running on the current node)

docker service ps web (shows all nodes where web is running)

goto localhost:8080 and check out how containers servicing the page are changing at each refresh

docker service scale web=10 (scaling up) 
 (use this also for scaling down. Dont go through side door)

docker container rm #cid #cid ..
(side door destruction)

docker container ls
(new containers automatically created making up for lost ones)
(done by reconciallation loop which constantly monitors the desired state with current state available)













