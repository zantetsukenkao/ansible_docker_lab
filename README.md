# ansible_docker_lab



## Getting started

To make it easy for you to get started with this lab, here's a list of recommended next steps.


## Add your files



```
cd existing_repo
```
 use docker-compose if you use the python version of docker compose
```
docker compose up -d --build
docker network inspect ansible_docker_lab_my_network
IP1=$(docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' ansible_node1)
IP2=$(docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' ansible_node2)
```
edit the inventory file with the ip@ of the tow nodes
```
sed -i "s/ipNode1/$IP1/g; s/ipNode2/$IP2/g" inventory
```
edit the myscript.sh with the ip@ of the nodes
```
sed -i "s/ipNode1/$IP1/g; s/ipNode2/$IP2/g" myscript.sh
```
copy the inventoty file into ansible-server container
copy the myscript file into ansible-server container
```
./copytocontainer.sh

```
execute the copy of the public key to the nodes
```
docker compose exec -it ansible-manager ./myscript.sh
```
test ansible ping
```
docker compose exec -it ansible-manager ansible -i inventory node -m ping

```
