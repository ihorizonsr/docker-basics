# Dockerfile:

- Docker can build images automatically by reading the instructions from a Dockerfile.
- A Dockerfile must begin with a **FROM** instruction. The **FROM** instruction specifies the **Parent Image** from which you are building.
- The image is usually built by executing **Docker instructions**, which added **layers** on top of existing image.
- The final docker image can be considered as a layered structure where there is a core or a base image and on top of that, there are several layered intermediate images.

#### Let's start with the uses of the commands **RUN**, **CMD** and **ENTRYPOINT** in Dockerfile:

- All RUN, CMD and ENTRYPOINT commands have 2 forms (Shall & Executable):
- **Shell Form:** \<Instruction> \<command>
- **Executable Form:** <instruction>["executable","param1","param2",...]

## RUN:

RUN commands always executes in a new layer and creates a new image layer. It is often used for installing software packages and applications.
#### Shell Form:
```bash
<instruction> <command>
RUN apt-get -y update
```
#### Exectuable Form:
```bash
<instruction> ["executable","param1","param2",...]
RUN ["apt-get", "install", "apache2"]
```
#### Dockerfile:
```bash    
FROM ubuntu
RUN apt-get -y update
RUN apt-get install apache2 -y
```
```bash
docker build . -t ubuntu:run-v1
```
```bash
docker image ls
```
```bash
docker run -d --name run-cont1 ubuntu:run-v1
```
```bash
docker run -d --name run-cont2 ubuntu:run-v1
```
```bash
docker container ls -a
```
> **Please Note:** If there is no **ENTRYPOINT** or **CMD** specified in the Docker image, it starts and exits at the same time that means container stops automatically. It is essential to specify **ENTRYPOINT** or **CMD** so that when you will start the container, it should execute something rather than just start and stop the container.

## CMD:

CMD commands allows to set default command and/or parameter. This will be executed if you run a particular container without specifying some command, which can be overwritten from command line when docker container runs. 

#### Shell Form:
```bash
CMD command param1 param2
CMD echo "Hello World"
```
#### Exectuable Form:
```bash
CMD ["executable","param1","param2",...]
CMD ["/bin/echo", "Hello World"]
```
#### Dockerfile:
```bash
FROM ubuntu:trusty

CMD ping localhost
```
```bash
docker build . -t cmd-ping
docker run cmd-ping
docker run cmd-ping hostname
```

```bash
FROM ubuntu:latest

RUN apt-get update && \
    apt-get install -y apache2-utils && \
    rm -rf /var/lib/apt/lists/*

CMD ["ab"]

docker image build . -t cmd-ab
docker run cmd-ab
docker run cmd-ab ab http://bencane.com/
docker run entry-ab ab -n 100 -c 10 http://bencane.com/
docker run cmd-ab echo "Hello World"
```

## ENTRYPOINT

ENTRYPOINT command is similar to CMD, however it configures a container that will run as an executable form.  If you want to run a container with the condition that a particular command is always executed, use ENTRYPOINT.

#### Shell Form:
```bash
ENTRYPOINT command param1 param2
ENTRYPOINT echo "Hello World"
```
#### Executable Form:
```bash
ENTRYPOINT ["executable","param1","param2",...]
ENTRYPOINT ["/bin/echo", "Hello World"]
```
> Executable form of ENTRYPOINT allows you to set commands and parameters and then use either form of CMD to set addtional parameters that are more likely to be changed

#### Dockerfile:
```bash
FROM alpine
ENTRYPOINT ["/bin/echo", "Hello"]
CMD ["World"]
```

#### Dockerfile:
```bash
FROM alpine

RUN apk add --force python

CMD ["www.google.com"]

ENTRYPOINT [ "ping","-c", "5", "-s", "1000"]
```
```bash
docker build . -t epoint-ping
```
```bash
docker run epoint-ping
```
```bash
docker run epoint-ping 4.4.4.4
```
```bash
FROM ubuntu:latest

RUN apt-get update && \
    apt-get install -y apache2-utils && \
    rm -rf /var/lib/apt/lists/*

ENTRYPOINT ["ab"]

docker run ab http://bencane.com/
docker run entry-ab -n 100 -c 10 http://bencane.com/
docker run entry-ab echo "Hello World"
```

## COPY & ADD Directives:

When creating Dockerfiles, it’s often necessary to transfer files from the host system into the Docker image. These could be property files, native libraries, or other static content that our applications will require at runtime.

The Dockerfile specification provides two ways to copy files from the source system into an image: the **COPY** and **ADD** directives.
Here we will look at the difference between them and when it makes sense to use each one of them.

## **COPY Directive:**
COPY takes in a source and destination. It only lets you copy in a local or directory from your host (the machine-building the Docker image) into the Docker image itself.
```bash
COPY <source> <destination>
```
We can specify multiple source paths and we need to use a relative path while specifying multiple sources. We can use wildcards to specify the source as well. We can specify the destination as an absolute path or relative to the WORKDIR directive if the WORKDIR directive is defined in the Dockerfile. We can change the ownership of the files or directories while copying it to the container filesystem.

#### Dockerfile - Sample
```bash
FROM httpd:2.4
COPY . /usr/local/apache2/htdocs/
```
```bash
docker build . -t apache:copy-v1
```
```bash
docker image ls
```
```bash
docker run -t -d -P --name copy-cont apache:copy-v1
```
```bash
docker container ls
```
> Open Browser and Enter IP:PORT and verify the site

## **ADD Directive:**

**ADD**  does the same as **CMD** but in addition, it also supports 2 other sources. 

- A URL instead of a local file/directory.
- Auto extract tar from the source directory into the destination.

```bash
ADD <source> <destination>
```
> A valid use case for ADD is when we want to extract a local tar file into a specific directory in your Docker image.

#### Dockerfile - Sample
```bash
FROM httpd:2.4
ADD website.tar.gz /usr/local/apache2/htdocs/
```
```bash
docker build . -t apache:add-v1
```
```bash
docker image ls
```
```bash
docker run -t -d -P --name add-cont apache:add-v1
```
```bash
docker container ls
```
> Open Browser and Enter IP:PORT and verify the site


#### When to use **ADD** or **COPY**: 
> According to the Dockerfile best practices guide, we should always prefer COPY over ADD unless we specifically need one of the two additional features of ADD. As noted above, using ADD command automatically expands tar files and specific compressed formats, which can lead to unexpected files being written to the file system in our images.

## **VOLUME:**
Volumes are the preferred mechanism for persisting data generated by and used by Docker containers. While bind mounts are dependent on the directory structure and OS of the host machine, volumes are completely managed by Docker. Volumes have several advantages over bind mounts:

- Volumes are easier to back up or migrate than bind mounts.
- You can manage volumes using Docker CLI commands or the Docker API.
- Volumes work on both Linux and Windows containers.
- Volumes can be more safely shared among multiple containers.
- Volume drivers let you store volumes on remote hosts or cloud providers, to encrypt the contents of volumes, or to add other functionality.
- New volumes can have their content pre-populated by a container.
- Volumes on Docker Desktop have much higher performance than bind mounts from Mac and Windows hosts.

> In addition, volumes are often a better choice than persisting data in a container’s writable layer, because a volume does not increase the size of the containers using it, and the volume’s contents exist outside the lifecycle of a given container.

#### List all volumes
```bash
docker volume ls
```
#### Create Docker Volume
```bash
docker volume create nginx-vol
```
#### Mount the volume to container
```bash
docker run -t -d -P --name vol-container1 -v nginx-vol:/usr/share/nginx/html nginx:latest
```
#### Find container exposed port
```bash
docker container ls
```
> Open browser and enter IP:PORT and Verify Nginx Site up and running
```bash
docker cp index.html vol-container1:/usr/share/nginx/html
```
> Open browser and enter IP:PORT and Verify Nginx Site with modified index page.
```
docker inspect vol-container1
```
> Verify the Mount details
  
#### Share volume between containers
```bash
docker run -t -d -P --name vol-container2 -v nginx-vol:/usr/share/nginx/html nginx:latest
```
#### Stop and Remove Containers
```bash
docker container ls -a
docker container stop vol-container1 & vol-container2
docker container rm vol-container1 & vol-container2
docker container ls -a
```
#### Create and Run new container with same Volume mount
```bash
docker run -t -d -P --name vol-container -v nginx-vol:/usr/share/nginx/html nginx:latest
```
> Open browser and enter IP:PORT and Verify Nginx Site with modified index page.

### Mount Host directory into the container

```bash
docker run -d --name dir-container -v <Source Path>:<Destination Path> nginx:latest
```
```bash
docker run -d --name dir-container -v D:\data:/app nginx:latest
```
```bash
docker exec -it dir-container /bin/bash
```
> Verify the mount path /app

> Volume Location - Windows Explorer: \\\wsl$\docker-desktop-data\data\docker\volumes

## Docker Document Reference:
- [Docker Volumes](https://docs.docker.com/storage/)
- [Dockerfile Reference](https://docs.docker.com/engine/reference/builder/)

---

### [<<Back](https://github.com/ihorizonsr/docker-basics/tree/main/docker-container) &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;[Next>>](https://github.com/ihorizonsr/docker-basics/tree/main/docker-registry)
