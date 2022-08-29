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
### Run an Image in a container
```bash
docker run --name ihz-nginx -d -p 8080:80 nginx
```
> - ***docker run***: The command first creates a writeable container layer over the specified image[nginx], and then starts it using the specified command.
> - ***-d***: Docker container runs in the background of the terminal.
> - ***-p***: Expose port 80 [internally accessable] to host or outside with 8080 [exterally accessable]
> - ***--name***: Assign a name to the container

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
 
 


