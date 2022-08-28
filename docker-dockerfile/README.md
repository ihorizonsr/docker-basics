# Dockerfile:

## COPY & ADD Directives:

When creating Dockerfiles, it’s often necessary to transfer files from the host system into the Docker image. These could be property files, native libraries, or other static content that our applications will require at runtime.

The Dockerfile specification provides two ways to copy files from the source system into an image: the **COPY** and **ADD** directives.
Here we will look at the difference between them and when it makes sense to use each one of them.

#### **COPY Directive:**
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

#### **ADD Directive:**

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

#### When to use **ADD** or **COPY**: 
> According to the Dockerfile best practices guide, we should always prefer COPY over ADD unless we specifically need one of the two additional features of ADD. As noted above, using ADD command automatically expands tar files and specific compressed formats, which can lead to unexpected files being written to the file system in our images.

### **VOLUME:**
Volumes are the preferred mechanism for persisting data generated by and used by Docker containers. While bind mounts are dependent on the directory structure and OS of the host machine, volumes are completely managed by Docker. Volumes have several advantages over bind mounts:

- Volumes are easier to back up or migrate than bind mounts.
- You can manage volumes using Docker CLI commands or the Docker API.
- Volumes work on both Linux and Windows containers.
- Volumes can be more safely shared among multiple containers.
- Volume drivers let you store volumes on remote hosts or cloud providers, to encrypt the contents of volumes, or to add other functionality.
- New volumes can have their content pre-populated by a container.
- Volumes on Docker Desktop have much higher performance than bind mounts from Mac and Windows hosts.

> In addition, volumes are often a better choice than persisting data in a container’s writable layer, because a volume does not increase the size of the containers using it, and the volume’s contents exist outside the lifecycle of a given container.

#### Dockerfile - Sample
```bash
FROM httpd:2.4
Volume:
```
### **RUN:**
The **docker run** command is used to run or start a command in a new container which means it creates a writeable layer on top of the mentioned image in the command. That’s why we call a container is a writeable image. This is the first command that we run when start learning Docker. There are a lot of options available with this command to configure the container as per our requirement like running a container in detached mode or interactive mode, specifying a name to the container, attaching network, volume, etc., exposing port to access the containers’ application externally, and many more things.

> ### How run Command Works in Docker?
When we run the **docker run** command on the terminal, Docker daemon searches for the mentioned Docker image locally and if it finds the image locally then it creates a writeable layer over the specified Docker image and starts the container using specified command and if it does not find the image locally then it firsts pull that image from the registry and by default, it goes to **hub.docker.com** if there is no local registry mentioned in the daemon.json file.

    docker run -d -e "USER=test1" --name web-nginx nginx

### **CMD:**
Docker CMD defines the default executable of a Docker image. You can run this image as the base of a container without adding command-line arguments. In that case, the container runs the process specified by the CMD command.

The CMD instruction is only utilized if there is no argument added to the run command when starting a container. Therefore, if you add an argument to the command, you override the CMD.


### **ENTRYPOINT:**

Docker ENTRYPOINT is a Dockerfile directive or instruction that is used to specify the executable which should run when a container is started from a Docker image. It has two forms, the first one is the **exec** form and the second one is the **shell** form. If there is no entrypoint or CMD specified in the Docker image, it starts and exits at the same time that means container stops automatically so, we must have to specify entrypoint or CMD so that when we will start the container it should execute something rather than going to stop.

### Dockerfile - Sample
```bash
FROM alpine
RUN apk add python
CMD ["8.8.8.8"]
ENTRYPOINT [ "ping", "-t", "5" ] 
```

## Docker Document Reference:
- <https://docs.docker.com/storage/volumes/>

---

### [Next>>](https://github.com/ihorizonsr/docker-basics/tree/main/docker-registry) &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;[<<Back](https://github.com/ihorizonsr/docker-basics/tree/main/docker-container)