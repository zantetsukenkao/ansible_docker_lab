ansible_docker_lab
Getting started
To make it easy for you to get started with this lab, here's a list of recommended next steps.

build and configure your envirement
cd existing_repo
use docker-compose if you use the python version of docker compose

docker compose up -d --build
docker network inspect ansible_docker_lab_my_network
IP1=$(docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' ansible_node1)
IP2=$(docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' ansible_node2)
edit the inventory file with the ip@ of the tow nodes

sed -i "s/ipNode1/$IP1/g; s/ipNode2/$IP2/g" inventory
edit the myscript.sh with the ip@ of the nodes

sed -i "s/ipNode1/$IP1/g; s/ipNode2/$IP2/g" myscript.sh
copy the inventoty file into ansible-server container copy the myscript file into ansible-server container

./copytocontainer.sh

execute the copy of the public key to the nodes

docker compose exec -it ansible-manager ./myscript.sh
test ansible ping

docker compose exec -it ansible-manager ansible -i inventory node -m ping

install nginx on the nodes with the PASSWORD: password

docker cp install_nginx.yml ansible_server:/
docker compose exec ansible-manager ansible-playbook -i inventory install_nginx.yml --ask-become-pass
start the nginx servers on the nodes

docker cp start_nginx.yml ansible_server:/
docker compose exec ansible-manager ansible-playbook -i inventory start_nginx.yml --ask-become-pass
test the acces to nginx on the nodes

 curl $IP1:8080
 curl $IP2:8080
