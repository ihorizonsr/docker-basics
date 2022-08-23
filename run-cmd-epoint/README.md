# Docker RUN - CMD - ENTRYPOINT

### RUN
The **docker run** command is used to run or start a command in a new container which means it creates a writeable layer on top of the mentioned image in the command. That’s why we call a container is a writeable image. This is the first command that we run when start learning Docker. There are a lot of options available with this command to configure the container as per our requirement like running a container in detached mode or interactive mode, specifying a name to the container, attaching network, volume, etc., exposing port to access the containers’ application externally, and many more things.

> ### How run Command Works in Docker?
When we run the **docker run** command on the terminal, Docker daemon searches for the mentioned Docker image locally and if it finds the image locally then it creates a writeable layer over the specified Docker image and starts the container using specified command and if it does not find the image locally then it firsts pull that image from the registry and by default, it goes to **hub.docker.com** if there is no local registry mentioned in the daemon.json file.

    docker run -d -e "USER=test1" --name web-nginx nginx

### CMD
Docker CMD defines the default executable of a Docker image. You can run this image as the base of a container without adding command-line arguments. In that case, the container runs the process specified by the CMD command.

The CMD instruction is only utilized if there is no argument added to the run command when starting a container. Therefore, if you add an argument to the command, you override the CMD.


### ENTRYPOINT

Docker ENTRYPOINT is a Dockerfile directive or instruction that is used to specify the executable which should run when a container is started from a Docker image. It has two forms, the first one is the **exec** form and the second one is the **shell** form. If there is no entrypoint or CMD specified in the Docker image, it starts and exits at the same time that means container stops automatically so, we must have to specify entrypoint or CMD so that when we will start the container it should execute something rather than going to stop.

### Example: Dockerfile
    FROM alpine
    RUN apk add python
    CMD ["8.8.8.8"]
    ENTRYPOINT [ "ping", "-t", "5" ] 