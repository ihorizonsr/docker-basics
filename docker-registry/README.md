# Docker Registry
The Registry is a stateless, highly scalable server side application that stores and lets you distribute Docker images. The Registry is open-source, under the permissive [Apache license](https://en.wikipedia.org/wiki/Apache_License)

Docker registry is an excellent way to supplement and integrate your CI/CD pipelines. Whenever there is a new commit in your source code or version control system, the CI workflow is triggered which then deploys the image to your registry if the CI workflow completion was successful. A signal from the Registry would then initiate a staging environment deployment or alert other systems to the availability of a new image.

So essentially we can say:

1. Docker Registry aids in development automation. The docker registry allows you to automate building, testing, and deployment. Docker registry may be used to create faster CI/CD pipelines, which helps to reduce build and deployment time.
2. Docker Registry is useful if you want complete control over where your images are kept. A private Docker registry can be used. You gain total control over your applications by doing so. In addition to controlling who may access your Docker images, you can determine who can view them.
3. Docker Registry can provide you with information about any issue you may encounter. You may also completely rely on it for container deployment and access it at any moment.

### Alternates of Docker Registry:
Following are some of the alternatives of Docker Registry: 

1. [Docker Hub](https://hub.docker.com/) is a service provided by Docker for finding and sharing container images with your team. It is the world’s largest repository of container images with an array of content sources including container community developers, open source projects and independent software vendors (ISV) building and distributing their code in containers.

```bash
docker login
```

> **Dockerfile:**

```bash
FROM httpd:2.4

COPY . /usr/local/apache2/htdocs/
```
> **docker build -t \<username>/\<repo-name>:\<tagname>**
```bash
docker build -t ihorizons/ra-apache:v1
```
```bash
docker run -d -P --name ra-apache ihorizons/ra-apache:v1 #Test the build image
```
```bash
docker push ihorizons/ra-apache:v1
docker image rm ihorizons/ra-apache:v1
docker pull ihorizons/ra-apache:v1
docker run -d -P --name ra-apache ihorizons/ra-apache:v1
```

2. Few other alternates for Docker Registry are: 
    - JFrog Bintray i.e a cloud platform that provides services of managing, deploying, and promoting your applications.
    - Gitlab Container Registry, which is a private and highly secure repository for storing docker images.



Users get access to free public repositories for storing and sharing images or can choose a subscription plan for private repositories.

### **Clould & Other Registry:**
- Azure Container Registry
- Google Container Registry
- Google Artifact Registry
- Amazon EC2 Container Registry
- Bintray.io/Artifactory
- Quay.io
- Github Container Registry

## Reference:
- [Docker Hub Quick Start](https://docs.docker.com/docker-hub/)
- [Push your first image to your Azure container registry using the Docker CLI](https://docs.microsoft.com/en-us/azure/container-registry/container-registry-get-started-docker-cli?tabs=azure-cli)
---

### [<<Back](https://github.com/ihorizonsr/docker-basics/tree/main/docker-dockerfile)
