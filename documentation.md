# Hotel-Booking-System
Hotel Booking System Application for hotel reservations management

Booking dockerized website using Oracle 21c & Spring Boot and React 

## Technology stack  
- **Deployment**: Docker Compose v2.12.2 (Docker Engine - Community v20.10.21)
- **Backend**: Spring Boot 3.1.0  (Java 20)
- **Database**: Oracle Database (21c)
- **Frontend**: React 18.2
- **Styling**: Bootstrap4

## Setting up OS Requirements
1. Install Docker on your OS. 
⚠️ Check your Docker Compose version by running `docker compose version`. Expected output: `Docker Compose version v2.6.0`.

2. Follow instructions at [Post-installation steps for Linux (Manage Docker as a non-root user)](https://docs.docker.com/engine/install/linux-postinstall/#manage-docker-as-a-non-root-user) in order to be able to run Docker without `root` privileges. Afterwards, run these two commands 
```
 sudo systemctl enable docker.service
 sudo systemctl enable containerd.service
```
in order to ensure the Docker service starts on boot.

## _Development_ environment

Commands to [+create+] / [-destroy-] the **development** environment: 
```
 # Build images from .yml file & start containers (services) 🔼
 docker compose -f ./docker-compose.dev.yml up -d --build  
```
   
```
 # Stop & delete containers (services) 🔽
 docker compose -f ./docker-compose.dev.yml down
```
Commands to [+start+] / [-stop-] the **development** environment:
```
 # Start containers (services) ✅, after they have been stopped using the 'stop' command 
 docker compose -f ./docker-compose.dev.yml start  
```
   
```
 # Stop containers (services) ❎, WITHOUT deleting them 
 docker compose -f ./docker-compose.dev.yml stop
```
Use `stop` when leaving for the day.  
Use `start` when you start working.  
Use `up -d --build` only when the `docker-compose.dev.yml` file is changed.


#### **Developer Admin Setup**

- Login with the credentials defined in the docker-compose file, associated with the oracle container
- Register a new Server connection
- In the connection Tab,the hostname is the db container's name, credentials are defined in the docker-compose file asscoiated with the db container

#### **Setup**

## **Extra** commands
Force build images & start containers for an environment: 
```
 docker compose -f ./docker-compose.dev.yml up -d --build --remove-orphans --force-recreate
```
Force rebuild of **ONLY ONE** service: 
```
 docker compose -f ./docker-compose.de.yml build <service name>
```
List all images on the host system: 
```
 docker image list -a
```  
List all containers (running or stopped): 
```
 docker container list -a
```   
Clean up leftover images after several consecutive builds in order to free up disk space (the cache is also discarded): 
```
 docker rmi $(docker images -q -f dangling=true)
 docker builder prune
```
Inspect the logs of a container that **is currently running**:
```
 docker-compose logs -f [container id|container name]
```
Get a shell inside of a container
```
 docker exec -it <container name> /bin/bash
```

