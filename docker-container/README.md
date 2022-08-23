# Docker Container

Docker Container is a standardized unit which can be created on the fly to deploy a particular application or environment. It could be an Ubuntu container, CentOs container, etc. to full-fill the requirement from an operating system point of view. Also, it could be an application oriented container like CakePHP container or a Tomcat-Ubuntu container etc.

#### Below are the basic commands which should be know to developers and system admins.

### List containers
-     docker container ls
-     docker ps -a

### Difference between docker *run* and docker *container run*
They are exactly the same. Prior to docker 1.13 the docker run command was only available. The CLI commands were then refactored to have the form docker COMMAND SUBCOMMAND, wherein this case the COMMAND is container and the SUBCOMMAND is run. This was done to have a more intuitive grouping of commands since the number of commands at the time has grown substantially.

### Run an Image in a container and rename the container
-     docker run -d --name ihz-linux alpine watch "date >> /var/log/date.log"
-     docker rename ihz-linux alpine-linux
### Running an Interactive & Non-Interactive Shell in a Docker Container
-     docker exec -it alpine-linux sh
> If the container image includes a more advanced shell such as bash, we can replace sh with bash above.
-     exit
-     docker exec alpine-linux tail /var/log/date.log

### Running Commands in an Alternate Directory in a Docker Container
-     docker exec --workdir /tmp alpine-linux pwd

### Start or Stop container
-     docker container stop alpine-linux 
-     docker container start alpine-linux

### Remove container
-     docker rm alpine-linux

### Prune – remove all stopped containers
-     docker container prune 

## Docker Document References:
-   <https://docs.docker.com/engine/reference/commandline/container/>