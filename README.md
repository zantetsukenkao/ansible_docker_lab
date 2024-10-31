# ansible_docker_lab



## Getting started

To make it easy for you to get started with this lab, here's a list of recommended next steps.


## Add your files



```
cd existing_repo
docker compose up -d --build ( or docker-compose if you use the python version of docker compose)
docker network inspect ansible_docker_lab_my_network
edit the inventory file with the ip@ of the tow nodes
edit the myscript.sh with the ip@ of the nodes
copy the inventoty file into ansible-server container
docker cp inventory ansible_server:/
copy the myscript file into ansible-server container
docker cp myscript.sh ansible_server:/
execute the copy of the public key to the nodes
docker compose exec -it ansible-manager ./myscript.sh
test ansible ping
docker compose exec -it ansible-manager ansible -i inventory node -m ping

```
