# Docker COPY - ADD - Volume

### COPY
Docker Copy is a directive or instruction that is used in a Dockerfile to copy files or directories from local machine to the container filesystem where the source is the local path and destination is the path in the container filesystem. We can specify multiple source paths and we need to use a relative path while specifying multiple sources. We can use wildcards to specify the source as well. We can specify the destination as an absolute path or relative to the WORKDIR directive if the WORKDIR directive is defined in the Dockerfile. We can change the ownership of the files or directories while copying it to the container filesystem.


### ADD

### Volume