# LOCAL REGISTRY
*  docker run -d -p 5000:5000 --restart=always --name registry registry:2

# JENKINS run with docker

### Run container :
* docker run -d --name jenkins -u root  --net=host -p 8080:8080 -v /data/jenkins:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock

### GET Secrets Password :

* docker exec -it jenkins cat /var/jenkins_home/secrets/initialAdminPassword

# JENKINS RUN DOCKER COMPOSE
* docker-compose -f "docker-compose.yml" up -d --build

# Helpers 
## Get process by port (windows)
* netstat -aon | findstr port 
## Kill process by pid (windows)
* taskkill /F /PID pid_number
## Send image to ssh host
* docker save my_image | ssh -C user@my.remote.host.com docker load


# Jenkins docker
* Jenkins CI with docker client

## DockerHub
- https://hub.docker.com/repository/docker/jcmds/jenkins-docker

## How to run

```
# open terminal and execute:

docker run -p 8080:8080 -p 50000:50000 \
-v /var/jenkins_home:/var/jenkins_home \ 
-v /var/run/docker.sock:/var/run/docker.sock \
-d --name jenkins jcmds/jenkins-docker:latest
```
## Set chmod
```
# open terminal and execute:

sudo chmod 777 /var/run/docker.sock