# Docker notes

### What is docker?

An open-source [containerization](https://github.com/JamesC830/tech503_docker_notes/blob/main/Containerization.md) platform.

### Virtualisation & Containers

***What is virtualisation?***

Virtualisation is the process of creating virtual versions of physical hardware resources, such as servers, storage devices, or network resources. It allows multiple virtual machines (VMs) to run on a single physical machine, each with its own operating system and applications.

***tldr***: Simulating a computer inside a computer

***What is a hypervisor and what does it enable?***

- A hypervisor is software that creates and manages virtual machines
- Hypervisors enable multiple VMs to share the same physical resources while maintaining isolation and independence.

***tldr***: Allocates compute to VMs

***How does virtualisation work?***

Virtualisation works by abstracting the physical hardware using a hypervisor, which allocates resources to each VM. Each VM operates as if it has its own dedicated hardware, with its own operating system and applications.

***What does virtualisation actually do?***

Virtualisation maximises resource utilisation, improves scalability, enhances disaster recovery, and enables efficient testing and development environments.

***What are the disadvantages of virtualisation?***

- Performance: Not all applications perform well in virtualised environments
- Complexity
- Running multiple VMs can consume significant resources.
- Single point of failure: OS or hardware or hypervisor

***What is containerisation and how is it different from virtualisation?***

Containerisation involves encapsulating an application and its dependencies into a container, which runs on a shared operating system kernel. Unlike VMs, containers do not require a full operating system, making them more lightweight and faster to start.

***Why would you choose containers over virtual machines?***

- Containers are more lightweight, so consume fewer resources
- Speed: Containers are faster to start up
- Portability: Containers can run consistently across different environments

### Docker Basics

***What is a Docker image and how is it related to a container?***

A Docker image is a read-only template that contains the application and its dependencies. A container is a running instance of an image.

***What does the command docker run hello-world do?***

This command runs a container from the hello-world image, which is designed to test Docker installations.

***What does the -it flag do in docker run -it ubuntu bash?***

Makes the interface interactive

***How do you list running Docker containers? What’s the difference when using the -a flag?***

```docker ps``` - Lists running containers

```docker ps``` - Lists all containers (including non running containers)

***How do you run an Ubuntu container in detached mode using Docker?***

```docker run -d``` - The ```-d``` flag means detached

***How do you execute a command inside a running Docker container (e.g. check the current user)?***

```docker exec -it <container_id> <command>```

```docker exec -it <container_id> whoami``` - Checks the current user

***How do you attach your terminal to a running Docker container?***

```docker attach <container_id>```

***How do you stop a running Docker container?***

```docker stop <container_id>```

***How do you remove a Docker container?***

```docker rm <container_id>```

```docker rm -f <container_id>``` - Forcefully removes (not recommended)

***How do you list all Docker images available locally?***

```docker images```

***How do you remove a specific Docker image (e.g. ubuntu)?***

```docker rmi ubuntu```

***How do you force-remove a Docker image even if it’s in use?***

```docker rmi -f <image_id>```

### Docker Registries & Repositories

***What is the local image registry in Docker?***

Where Docker stores images on your local machine.

***What is DockerHub?***

DockerHub is a cloud-based registry service where Docker users can share and access container images.

***What does the command docker pull nginx do?***

Downloads nginx from DockerHub to your local machine

***How do you run an Nginx container in detached mode?***

```docker run -d nginx```

### Networking & Port Mapping

***What is the OSI model in networking?***

![osi](https://cf-assets.www.cloudflare.com/slt3lc6tev37/6ZH2Etm3LlFHTgmkjLmkxp/59ff240fb3ebdc7794ffaa6e1d69b7c2/osi_model_7_layers.png)

***What is a network port?***

A virtual communication endpoint within a computer or network device, identified by a unique number

***How does Docker handle port mapping?***

Docker maps ports from the host machine to the container using the ```-p``` flag in the ```docker run``` command

***What does the command ```docker run -d -p 5000:80 nginx``` do?***

This command runs an Nginx container in detached mode and maps port 80 inside the container to port 5000 on the host machine.

***How can you find out which port your Docker container is running on?***

```docker ps``` - There is a ports column

### File Management in Docker

***How do you copy a file from your local machine into a Docker container?***

```docker cp /path/on/host <container_id>:/path/in/container```

***What command is used to save container changes as a new image?***

```docker commit```

***How do you commit changes from a container to a new Docker image?***

```docker commit <container_id> new_image_name```

***How do you push a Docker image to a remote repository like DockerHub?***

1. ```docker login```
2. ```docker tag my_image username/my_image``` -  Tag the image with your docker username
3. ```docker push username/my_image``` - Push the image

### Dockerfile Essentials

***What is a Dockerfile and what is it used for?***

A Dockerfile is a text file containing a set of instructions that tells Docker how to build a custom image.

***What is the format for construction arguments in a Dockerfile?***

```ARG variable=value```

***What is the purpose of the ```FROM``` instruction in a Dockerfile?***

Sets the base image for the docker image

***What does the ```EXPOSE``` instruction do in a Dockerfile?***

It documents which port the container will use at runtime

***What is the structure of a ```COPY``` instruction in a Dockerfile?***

```COPY <source> <destination>```

```COPY ./app /usr/src/app``` - Example

***How do you build a Docker image from a Dockerfile?***

```docker build -t my_image_name .```

The ```.``` refers to the current directory containing the Dockerfile.

***How do you slim down a Docker image to reduce its size?***

- Use lightweight base images, e.g., alpine
- Clean up unnecessary files during the build
- Combine RUN statements to reduce layers
- Use .dockerignore to exclude unnecessary files from context
- Minimize dependencies and build tools in the final image
