# docker-images

Docker Image is an executable package of software that includes everything needed to run an application. It contains the definitions of all the libraries, binaries, configuration files, etc. It also referred to as snapshots because they are immutable.

#### Below are the basic commands which should be know to developers and system admins.

> ##### List out all images
> - docker image ls 

> ##### Pull Image from Docker Hub Repository - ImageName:TagName
> - docker image pull **nginx:latest**

> ##### Run an Image 
> docker run --name ihz-nginx -d -p 8080:80 nginx
>
> - The docker run command first creates a writeable container layer over the specified image, and then starts it using the specified command.
> - **-d** Image will run in detach mode - Docker container runs in the background of your terminal.

> docker image history ## Show history of an image

> docker image rm ## Remove images

> docker image prune ## Prune – remove unused images

> docker build ## Build an Image from Dockerfile

### Docker Document References

-   <https://docs.docker.com/engine/reference/commandline/image/>
-   <https://docs.docker.com/engine/reference/commandline/images/>
