# Docker Basics

Learn Docker container basics...

Docker is the leading open-source container service provider that has ruled the entire market since its inception. It’s easy to learn and makes the development and deployment of applications a piece of cake. However, when a beginner starts learning Docker containerization, it seems to be somewhat confusing because of certain terminologies that they come across such as containers, images, volumes, docker hub, docker-engine, registries, etc. In fact, if a beginner gets hold of two of the most important artifacts of Docker containerization - Docker Images and Docker Containers, then it’s easier for him/her to ace through the entire concept.

# Containerization vs Virtualization or Virtual Machine

<img width="557" alt="image" src="https://user-images.githubusercontent.com/111513801/185914093-401eb14a-698d-48bf-b862-29fc816251eb.png">

> **Virtualization** − Virtualization is the technology that can simulate your physical hardware (such as CPU cores, memory, disk) and represent it as a separate machine. It has its own Guest OS, Kernel, process, drivers, etc. Therefore, it is hardware-level virtualization. Most common technology is "VMware" and "Virtual Box".

> **Containerization** − Containerization is "OS-level virtualization". It doesn't simulate the entire physical machine. It just simulates the OS of your machine. Therefore, multiple applications can share the same OS kernel. Containers play similar roles as virtual machine but without hardware virtualization. Most common container technology is "Docker".

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

# Docker Architecture

<img width="491" alt="image" src="https://user-images.githubusercontent.com/111513801/185914743-20071a43-7a34-4aa6-ace1-a687bdfe2373.png">

