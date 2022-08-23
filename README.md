# Docker Basics

Learn Docker container basics...

Docker is the leading open-source container service provider that has ruled the entire market since its inception. It’s easy to learn and makes the development and deployment of applications a piece of cake. However, when a beginner starts learning Docker containerization, it seems to be somewhat confusing because of certain terminologies that they come across such as containers, images, volumes, docker hub, docker-engine, registries, etc. In fact, if a beginner gets hold of two of the most important artifacts of Docker containerization - Docker Images and Docker Containers, then it’s easier for him/her to ace through the entire concept.

# Containerization vs Virtualization or Virtual Machine

<img width="557" alt="image" src="https://user-images.githubusercontent.com/111513801/185914093-401eb14a-698d-48bf-b862-29fc816251eb.png">

Virtual Machine takes a lot of time to boot up because the guest operating system needs to start from scratch, which will then load all the binaries and libraries. This is time consuming and will prove very costly at times when quick startup of applications is needed. In case of Docker Container, since the container runs on your host OS, you can save precious boot-up time. This is a clear advantage over Virtual Machine.

Consider a situation where I want to install two different versions of PHP on your system. If you use Virtual Machine, It will need to set up 2 different Virtual Machines to run the different versions. Each of these will have its own set of binaries and libraries while running on different guest operating systems. Whereas if we use Docker Container, even though we will be creating 2 different containers where each container will have its own set of binaries and libraries, we will be running them on our host operating system. Running them straight on our Host operating system makes my Docker Containers lightweight and faster.


# Docker Architecture

<img width="491" alt="image" src="https://user-images.githubusercontent.com/111513801/185914743-20071a43-7a34-4aa6-ace1-a687bdfe2373.png">

