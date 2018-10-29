## Docker Guide 

Docker provides a way to run applications securely isolated in a container, packaged with all its dependencies and libraries.

Docker is a platform for developers and sysadmins to develop, deploy, and run applications with containers. The use of Linux containers to deploy applications is called containerization. Containers are not new, but their use for easily deploying applications is.

### Images and Container

A container is launched by running an image. An image is an executable package that includes everything needed to run an application--the code, a runtime, libraries, environment variables, and configuration files.

A container is a runtime instance of an image--what the image becomes in memory when executed (that is, an image with state, or a user process). You can see a list of your running containers with the command ``` docker ps``` just as you would in Linux.

### Testing Docker
Run  ```docker --version``` and ensure that you have a supported version of Docker.
