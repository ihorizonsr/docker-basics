# Docker Image

Docker Image is an executable package of software that includes everything needed to run an application. It contains the definitions of all the libraries, binaries, configuration files, etc. It also referred to as snapshots because they are immutable.

#### Below are the basic commands which should be know to developers and system admins.

### List out all images
-     docker image ls
-     docker images

### Pull an Image from Docker Hub Repository or Registry
-     docker pull nginx:latest
-     docker image pull nginx:latest

### Run an Image in a container
-     docker run --name ihz-nginx -d -p 8080:80 nginx
> - ***docker run***: The command first creates a writeable container layer over the specified image[nginx], and then starts it using the specified command.
> - ***-d***: Run image in detach mode i.e. Docker container runs in the background of the terminal.
> - ***-p***: Expose port 80 [access internally] to host or outside with 8080 [access exterally]
> - ***--name***: Assign a name to the container

### Show history of an image
-     docker image history nginx

### Remove images
-     docker image rm nginx
-     docker rmi nginx

### Prune – remove unused images
-     docker image prune 

### Build an Image from Dockerfile
-     docker build .

## Docker Document References:
-   <https://docs.docker.com/engine/reference/commandline/image/>
-   <https://docs.docker.com/engine/reference/commandline/images/>
