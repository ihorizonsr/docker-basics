# Docker Image

Docker Image is an executable package of software that includes everything needed to run an application. It contains the definitions of all the libraries, binaries, configuration files, etc. It also referred to as snapshots because they are immutable.

#### Below are the basic commands which should be know to developers and system admins.

### List out all images
```bash
docker image ls
```
```bash
docker images
```

### Pull an Image from Docker Hub Repository or Registry
```bash
docker pull nginx:latest
```
```bash
docker image pull nginx:latest
```
### **RUN:**
The **docker run** command is used to run or start a command in a new container which means it creates a writeable layer on top of the mentioned image in the command. That’s why we call a container is a writeable image. This is the first command that we run when start learning Docker. There are a lot of options available with this command to configure the container as per our requirement like running a container in detached mode or interactive mode, specifying a name to the container, attaching network, volume, etc., exposing port to access the containers’ application externally, and many more things.

> ### How run Command Works in Docker?
When we run the **docker run** command on the terminal, Docker daemon searches for the mentioned Docker image locally and if it finds the image locally then it creates a writeable layer over the specified Docker image and starts the container using specified command and if it does not find the image locally then it firsts pull that image from the registry and by default, it goes to **hub.docker.com** if there is no local registry mentioned in the daemon.json file.
```bash
docker run -d -e "USER=test1" --name web-nginx nginx
```
```bash
docker run --name ihz-nginx -d -p 8080:80 nginx
```
> ***-d***: Docker container runs in the background of the terminal.

> ***-p***: Expose port 80 [internally accessable] to host or outside with 8080 [exterally accessable]

> ***--name***: Assign a name to the container

### Show history of an image
```bash
docker image history nginx
```
### Remove images
```bash
docker image rm nginx
```
```bash
docker rmi nginx
```
### Prune – remove unused images
```bash
docker image prune 
```
### Build an Image from Dockerfile
```bash
docker build .
```
#### Dockerfile: Sample
```bash
FROM nginx:latest
CMD echo "Hello world!"
```

## Docker Document References:
-   <https://docs.docker.com/engine/reference/commandline/image/>
-   <https://docs.docker.com/engine/reference/commandline/images/>

---
### [<<Back](https://github.com/ihorizonsr/docker-basics#introduction-to-docker) &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;[Next>>](https://github.com/ihorizonsr/docker-basics/tree/main/docker-container)
 
 


