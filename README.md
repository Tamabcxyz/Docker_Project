# Docker_Project
#### Setup
```
install: https://docs.docker.com/engine/install/debian/
Or just donwlonad and run script:
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh

check version:
docker version
docker info
```

#### Pull images from docker hub: 
https://hub.docker.com/  
Only pull images                   
docker pull <images-name>         
Just do a quick pull and run            
docker run <images-name>

#### Run start a container
```
docker run image-name:tag (find image from local or pull from docker hub)
```
#### List images
```
docker images           
docker system df -v         
```
#### List containers
```
docker ps -a
```
#### Stop containers
```
docker stop <id-or-name-conatiner>
```
#### Remove containers
```
docker rm <id-or-name-conatiner>
```
#### Remove images
```
docker rmi id-or-name-images
```
#### Execute a command
```
docker exec name-container cat /etc/hosts
```
#### Attach and detach
```
docker run -d <images-name> (run detach mode, its will run in background)                    
docker attach <conatiner-id>          
docker run -it <images-name>  
```
#### Port mapping
```
docker run -p 80:5000 <images-name> (mapping port 80 from local to port 5000 in container)    
```
#### Volume mapping
```
docker run -v /opt/datadir:/var/lib/mysql mysql (mount /opt/datadir to /var/lib/mysql of docker host)
```
#### Inspect container
```
docker inspect <container-name>
```
#### Container logs
```
docker logs <container-name>
```
#### View the history of an image
```
docker history image-name:tag
```
#### Docker compose
```
have docker-compose.yml file         
docker-compose up    
```
Concept:
docker run -d --name=redis redis                
docker run -d --name=db postgres:9.4 
docker run -d --name=webapp -p 5000:80 mywebapp-image                
docker run -d --name=result -p 5001:80 result-app
docker run -d --name=worker worker      

link them together          
docker run -d --name=webapp -p 5000:80 --link redis:redis mywebapp 
docker run -d --name=result -p 5001:80 --link db:db result-app
docker run -d --name=worker --link db:db --link redis:redis worker      

#### Docker volumes
```
docker volume create data_volume (it's will create a folder under /var/lib/docker/volumes)          
```
#### Docker registry
Docker registry (docker.io) is a centralized storage and distribution system for Docker images. Docker hub all images is public. Docker registry can be public and private need to login (docker login)    
Change tag of an image an push to localhost    
```     
docker pull nginx:latest                
docker image tag nginx:latest localhost:5000/nginx:latest                          
docker push localhost:5000/nginx:latest         
```
#### Storage drivers
AUFS                    
ZFS              
BTRFS                  
Device Mapper                  
Overlay          
Overlay2             

#### Docker networking
- Bridge (default)
    by default docker only have one bridge, but user can be create by using docker network  
    ```            
    ex: docker network create \         
        --driver bridge \           
        --subnet ip \           
        custom-network     
    
    to chek run: docker network ls
    ```               
- None (docker run ubuntu --network=none)           
- Host (docker run ubuntu --network=host)     

##### Check the network info
```
docker network inspect bridge
docker network inspect host
docker network inspect none
```
##### Attach container to network
```
docker network connect <network_name> <container_name_or_id> (container is exist)   
docker run --network=<network_name> --name=<name-container> name-image (container is not exist)     
```
What location are the files related to the docker containers and images stored?     
==>/var/lib/docker

After pull new image that image will update at /var/lib/docker/aufs/diff/

#### Docker swarm (connect many docker hosts together)
Docker Swarm provides orchestration capabilities for managing a cluster of Docker hosts. It allows you to define a desired state for your applications, and it takes care of deploying and maintaining that state across the cluster. All three Docker hosts will be joined to the swarm and will be connected together using an overlay network. 
```      
- Docker host 1: docker swarm init              
- Docker host 2: docker swarm join --token <token>          
- Docker host 3: docker swarm join --token <token>              
- Docker host 4: docker swarm join --token <token>    

docker run my-web-server (it's create one instane, it mean one container)          
docker service create --replicas=3 my-web-server (it's create three instanes, it mean three container in cluster)      
docker service create --replicas=3 -p 8080:5000 my-web-server (same with docker run)                
```

#### Docker on Windows has two options

###### Docker on Windows using Docker Toolbox - Docker on Linux VM on Oracle Virtual Box on Windows            

Docker Toolbox Requirements         

64-bit operating system             

Windows 7 or Higher             

Virtualization enabled on Windows               

Docker Toolbox Contents             

Oracle Virtualbox               

Docker Engine               

Docker Machine              

Docker Compose              

Kitematic GUI                   

###### Docker For Windows - Docker on Linux VM on Windows Hyper-V on Windows

Docker For Windows Requirements         

Windows 10 Enterprise/Professional Edition              

Windows Server 2016             

Docker For Windows supports Linux Containers (Default) and Windows Containers               

Docker For Windows Container Types:                 

Windows Server Core: Windows container on native windows server core                

Hyper-V Isolation: Windows container on an isolated hyper-v kernel  

##### Create docker registry in local
```
mkdir registry
apt get update
apt-get install openssl
mkdir -p /tools/registry/ && cd /tools/registry
mkdir data certs
openssl req -newkey rsa:4096 -nodes -sha256 -keyout certs/domain.key -subj "/CN=192.168.1.100" -addext "subjectAltName = DNS:192.168.1.100,IP:192.168.1.100" -x509 -days 365 -out certs/domain.crt
vi docker-compose.yml
    version: '3'
    services:
    registry:
        image: registry:2
        restart: always
        container_name: registry-server
        ports:
        - "5000:5000"
        volumes:
        - ./data:/var/lib/registry
        - ./certs:/certs
        environment:
        REGISTRY_HTTP_TLS_CERTIFICATE: ./certs/domain.crt
        REGISTRY_HTTP_TLS_KEY: ./certs/domain.key
docker-compose up -d
docker-compose ps
docker login 192.168.1.100:5000 (failed to verify certificate)
mkdir -p /etc/docker/certs.d/192.168.1.100:5000/
cp certs/domain.crt /etc/docker/certs.d/192.168.1.100:5000/ca.crt
systemctl restart docker
docker login 192.168.1.100:5000 (OK)
#copy file domain.crt to client and do it again
```

##### Script install docker and docker compose
```
#!/bin/bash

sudo apt update
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
sudo apt install -y docker-ce
sudo systemctl start docker
sudo systemctl enable docker
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker --version
docker-compose --version
```
