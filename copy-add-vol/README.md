# Docker COPY - ADD - Volume

When creating Dockerfiles, it’s often necessary to transfer files from the host system into the Docker image. These could be property files, native libraries, or other static content that our applications will require at runtime.

The Dockerfile specification provides two ways to copy files from the source system into an image: the COPY and ADD directives.
Here we will look at the difference between them and when it makes sense to use each one of them.

### COPY
COPY takes in a source and destination. It only lets you copy in a local or directory from your host (the machine-building the Docker image) into the Docker image itself.

    COPY <source> <destination>

We can specify multiple source paths and we need to use a relative path while specifying multiple sources. We can use wildcards to specify the source as well. We can specify the destination as an absolute path or relative to the WORKDIR directive if the WORKDIR directive is defined in the Dockerfile. We can change the ownership of the files or directories while copying it to the container filesystem.

#### Example: Dockerfile
    FROM httpd:2.4
    COPY . /usr/local/apache2/htdocs/

### ADD
ADD  does the same but in addition, it also supports 2 other sources. 

A URL instead of a local file/directory.
Auto extract tar from the source directory into the destination.

    ADD <src> <dest>

> A valid use case for ADD is when we want to extract a local tar file into a specific directory in your Docker image.

#### Example: Dockerfile
    FROM httpd:2.4
    ADD website.tar.gz /usr/local/apache2/htdocs/

### When to use ADD or COPY: 
> According to the Dockerfile best practices guide, we should always prefer COPY over ADD unless we specifically need one of the two additional features of ADD. As noted above, using ADD command automatically expands tar files and specific compressed formats, which can lead to unexpected files being written to the file system in our images.

### Volume