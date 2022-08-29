# Docker Basics

Learn Docker container basics...

The documentation and the sample code arranged in a manner that anyone with little technical background can get started with Docker containerization, however little attention required. 

**Pre-requisite:** Please setup Docker Engine on your local system as mentioned in below links: 

> [Install Docker Desktop on Windows](https://docs.docker.com/desktop/install/windows-install/)

> [Install Docker Desktop on Linux](https://docs.docker.com/desktop/install/linux-install/)

> [Install Docker Desktop on Mac](https://docs.docker.com/desktop/install/mac-install/)

**Please Note:** If you are new to Docker or reading first time then first follow **order** as mentioned below in **Table of Content**  i.e. 1 to 5 to get best out of it.

## Table of Content:
1. [Introduction to Docker](https://github.com/ihorizonsr/docker-basics#introduction-to-docker)
2. [Docker Images](https://github.com/ihorizonsr/docker-basics/tree/main/docker-image)
3. [Docker Container](https://github.com/ihorizonsr/docker-basics/tree/main/docker-container)
4. [Docker Dockerfile](https://github.com/ihorizonsr/docker-basics/tree/main/docker-dockerfile)
5. [Docker Registry](https://github.com/ihorizonsr/docker-basics/tree/main/docker-registry)

# Introduction to Docker:

Docker is the leading open-source container service provider that has ruled the entire market since its inception. It’s easy to learn and makes the development and deployment of applications a piece of cake. However, when a beginner starts learning Docker containerization, it seems to be somewhat confusing because of certain terminologies that they come across such as containers, images, volumes, docker hub, docker-engine, registries, etc. In fact, if a beginner gets hold of two of the most important artifacts of Docker containerization - **Docker Images** and **Docker Containers**, then it’s easier for him/her to ace through the entire concept. Let's understand first in short, how containerization evolved.

Data centers consist of a large number of enterprise servers. Not all servers are active at the same time. In case traffic is directed mostly to a particular set of servers more, those servers get busy. The other servers are less loaded, or they even turn totally inactive, thereby wasting power, maintenance costs, and other allied resources.

With the changing times, businesses started looking for solutions to reduce overhead costs, enhance scalability, and standardize application deployment process. They started considering the following two approaches to reduce costs i.e. Virtualization & Containerization.

> **Virtualization:** Virtualization is the technology that can simulate the physical hardware (such as CPU cores, memory, disk) and represent it as a separate machine. It has its own Guest OS, Kernel, process, drivers, etc. Therefore, it is hardware-level virtualization. Most common technology is "VMware" and "Virtual Box".

> **Containerization:** Containerization is "OS-level virtualization". It doesn't simulate the entire physical machine. It just simulates the OS of the machine. Therefore, multiple applications can share the same OS kernel. Containers play similar roles as virtual machine but without hardware virtualization. Most common container technology is "Docker".

## Containerization vs Virtualization or Virtual Machine

<img alt="image" src="https://user-images.githubusercontent.com/111513801/185914093-401eb14a-698d-48bf-b862-29fc816251eb.png">

### Difference between Virtualization and Containerization
The following table compares and contrasts the different features of Virtualization and Containerization 

| Key Factor | Virtualization | Containerization |
|---|---|---|
| Technology | One physical machine has multiple OSs residing on it and appears as multiple machines. | The application developed in a host environment with same OS and the same machine executes flawlessly on multiple different environments. |
| Start-up Time | Higher than containers | Less |
| Speed of working | VMs being a virtual copy of the host server on its own operating system, VMs are resource-heavy, hence slower. | Containers are faster. |
| Size | Larger | Smaller |
| Component that Virtualizes and the one being virtualized | Hypervisors virtualize the underlying hardware (use of the same hardware). | Containers virtualize the operating system (use of the same OS). |
| Cost of implementation | Higher | Lower |
| Benefits for | IT enterprise businesses | Software developers and in turn IT businesses |

## Docker Architecture

As we now aware that Docker is the most popular containerization technology, so we should know littl details of its *Architecture, Components and Objects* as well.


<img alt="image" src="https://user-images.githubusercontent.com/111513801/185914743-20071a43-7a34-4aa6-ace1-a687bdfe2373.png">


The architecture of Docker uses a client-server model and consists of the Docker’s Client, Docker Host, Network and Storage components, and the Docker Registry/Hub. Let’s look at each of these in some detail.

### Docker’s Client
Docker users can interact with Docker through a client. When any docker commands runs, the client sends them to docker daemon, which carries them out. Docker API is used by Docker commands. It is possible for Docker client to communicate with more than one daemon.

### Docker Host
The Docker host provides a complete environment to execute and run applications. It comprises of the Docker daemon, Images, Containers, Networks, and Storage. As previously mentioned, the daemon is responsible for all container-related actions and receives commands via the CLI or the REST API. It can also communicate with other daemons to manage its services.

### Docker Objects 
1. ### Images
    Images are nothing but a read-only binary template that can build containers. They also contain metadata that describe the container’s capabilities and needs. Images are used to store and ship applications. An image can be used on its own to build a container or customized to add additional elements to extend the current configuration. 
    
    We can share the container images across teams within an enterprise with the help of a private container registry, or share it with the world using a public registry like Docker Hub. Images are the core element of the Docker experience as they enable collaboration between developers in a way that was not possible before

    #### [Docker Images](https://github.com/ihorizonsr/docker-basics/tree/main/docker-image)

2. ### Containers
    Containers are sort of encapsulated environments in which you run applications. Container is defined by the image and any additional configuration options provided on starting the container, including and not limited to the network connections and storage options. Containers only have access to resources that are defined in the image, unless additional access is defined when building the image into a container.

    We can also create a new image based on the current state of a container. Since containers are much smaller than VMs, they can be spun in a matter of seconds, and result in much better server density

    #### [Docker Containers](https://github.com/ihorizonsr/docker-basics/tree/main/docker-container)

3. ### Networks
    Docker networking is a passage through which all the isolated container communicate. There are mainly five network drivers in docker:

- **Bridge:** It is the default network driver for a container. We use this network when our application is running on standalone containers, i.e. multiple containers communicating with the same docker host.

-  **Host:** This driver removes the network isolation between docker containers and docker host. We can use it when we don’t need any network isolation between host and container.

-  **Overlay:** This network enables swarm services to communicate with each other. We use it when we want the containers to run on different Docker hosts or when we want to form swarm services by multiple applications.

-  **None:** This driver disables all the networking.

-  **macvlan:** This driver assigns mac address to containers to make them look like physical devices. It routes the traffic between containers through their mac addresses. We use this network when we want the containers to look like a physical device, for example, while migrating a VM setup.

4. ### Storage
     We can store data within the writable layer of a container but it requires a storage driver. Being non-persistent, it perishes whenever the container is not running. Moreover, it is not easy to transfer this data. With respect to persistent storage, Docker offers four options:

- **Data Volumes:** They provide the ability to create persistent storage, with the ability to rename volumes, list volumes, and also list the container that is associated with the volume. Data Volumes are placed on the host file system, outside the containers copy on write mechanism and are fairly efficient.

- **Volume Container:** It is an alternative approach wherein a dedicated container hosts a volume and to mount that volume to other containers. In this case, the volume container is independent of the application container and therefore you can share it across more than one container.

- **Directory Mounts:** Another option is to mount a host’s local directory into a container. In the previously mentioned cases, the volumes would have to be within the Docker volumes folder, whereas when it comes to Directory Mounts any directory on the Host machine can be used as a source for the volume.

- **Storage Plugins:** Storage Plugins provide the ability to connect to external storage platforms. These plugins map storage from the host to an external source like a storage array or an appliance. You can see a list of storage plugins on Docker’s Plugin page.

    #### [Docker Storage](https://github.com/ihorizonsr/docker-basics/tree/main/docker-dockerfile#volume)


### Docker’s Registry

Docker registries are services that provide locations from where we can store and download images. In other words, a Docker registry contains Docker repositories that host one or more Docker Images. Public Registries include two components namely the Docker Hub and Docker Cloud. We can also use Private Registries. The most common commands when working with registries include: docker push, docker pull, docker run. 

#### [Docker Registry](https://github.com/ihorizonsr/docker-basics/tree/main/docker-registry)

---

### [Next section](https://github.com/ihorizonsr/docker-basics/tree/main/docker-image)