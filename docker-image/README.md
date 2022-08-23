# docker-images

Docker Image is an executable package of software that includes everything needed to run an application. It contains the definitions of all the libraries, binaries, configuration files, etc. It also referred to as snapshots because they are immutable.

#### Below are the basic commands which should be know to developers and system admins.

> docker image ls

> docker image pull nginx:latest

> docker run --name ihz-nginx -d -p 8080:80 nginx

> docker image history ## Show history of an image

> docker image rm ## Remove images

> docker image prune ## Prune – remove unused images

> docker build ## Build an Image from Dockerfile

### Docker Document References

- https://docs.docker.com/engine/reference/commandline/image/  
- https://docs.docker.com/engine/reference/commandline/images/
