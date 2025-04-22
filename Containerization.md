# Containerization notes

### What is containerization?

A method of packaging an application and its dependencies into a single, isolated environment called a container, allowing it to run consistently across different systems and environments.

Alternatively:

A software deployment process that bundles an application’s code with all the files and libraries it needs to run on any infrastructure.

![Docker vs vm](https://bito.ai/wp-content/uploads/2023/01/image1-2.png)

### Benefits

- ***Portability***: Allows you to deploy an application in multiple environments without rewriting code.
- ***Scalability***: Containers are lightweight software components that run efficiently. For example, a virtual machine can launch a containerized application faster because it doesn't need to boot an operating system.
- ***Self-contained***: You can add multiple containers for different applications on a single machine. The container cluster uses computing resources from a shared operating system, but one container doesn't interfere with the operation of other containers. 
- ***Fault tolerance***: A single faulty container doesn't affect the other containers. This increases the resilience and availability of the application.
- ***Agility***: Software developers can troubleshoot and change the application code without interfering with the operating system, hardware, or other application services. They can shorten software release cycles and work on updates quickly with the container model.