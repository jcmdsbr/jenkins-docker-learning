# Jenkins Learning :sunglasses:

- Learning jenkins, basic to hero concepts!! using docker environment

## Give a Star! :star:

If you liked the project, please give a star ;)


## Run with docker ❗

```sh
docker run -p 8080:8080 -p 50000:50000 \
-v /var/jenkins_home:/var/jenkins_home \ 
-v /var/run/docker.sock:/var/run/docker.sock \
-d --name jenkins jcmds/jenkins-docker:latest

# docker run -d --name jenkins -u root  --net=host -p 8080:8080 -v /data/jenkins:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock
```

### GET Secrets Password 🔑

```sh
docker exec -it jenkins cat /var/jenkins_home/secrets/initialAdminPassword
```

## Run with docker compose 🚧

```sh
 docker-compose -f "docker-compose.yml" up -d --build
```

***CHMOD in docker.sock***

```sh
sudo chmod 777 /var/run/docker.sock
```
