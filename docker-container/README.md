# Docker Container

Docker Container is a standardized unit which can be created on the fly to deploy a particular application or environment. It could be an Ubuntu container, CentOs container, etc. to full-fill the requirement from an operating system point of view. Also, it could be an application oriented container like CakePHP container or a Tomcat-Ubuntu container etc.

#### Below are the basic commands which should be know to developers and system admins.

### List containers
```bash
docker container ls
```
```bash
docker ps -a
```
### Difference between docker *run* and docker *container run*
They are exactly the same. Prior to docker 1.13 the docker run command was only available. The CLI commands were then refactored to have the form docker COMMAND SUBCOMMAND, wherein this case the COMMAND is container and the SUBCOMMAND is run. This was done to have a more intuitive grouping of commands since the number of commands at the time has grown substantially.

### Run an Image in a container and rename the container
```bash
docker run -d --name ihz-linux alpine watch "date >> /var/log/date.log"
```
```bash
docker rename ihz-linux alpine-linux
```
### Running an Interactive & Non-Interactive Shell in a Docker Container
```bash
docker exec -it alpine-linux sh
```
> If the container image includes a more advanced shell such as bash, we can replace sh with bash above.
```bash
exit
```
```bash
docker exec alpine-linux tail /var/log/date.log
```
### Running Commands in an Alternate Directory in a Docker Container
```bash
docker exec --workdir /tmp alpine-linux pwd
```
### Running Commands as a Different User in a Docker Container
```bash
docker exec --user guest alpine-linux whoami
```

### Passing Environment Variables into a Docker Container
```bash
docker exec -e TEST=DevOps alpine-linux env
```
```bash  
docker exec -e TEST=DevOps -e ENVIRONMENT=prod alpine-linux env
```
```bash
docker exec --env-file .env alpine-linux env
``` 

### Start or Stop or Restart container
> Stop one or more running containers
```bash
docker container stop alpine-linux
```
> Start one or more stopped containers
```bash
docker container start alpine-linux
```
> Restart one or more containers
```bash
docker container restart alpine-linux
```

### Remove stopped container
```bash
docker rm alpine-linux
```
### Prune – remove all stopped containers
```bash
docker container prune 
```
## Docker Document References:
-   <https://docs.docker.com/engine/reference/commandline/container/>

---

### [Next>>](https://github.com/ihorizonsr/docker-basics/tree/main/run-cmd-epoint) &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;[<<Back](https://github.com/ihorizonsr/docker-basics/tree/main/docker-image)
