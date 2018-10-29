## Docker Guide 

Docker provides a way to run applications securely isolated in a container, packaged with all its dependencies and libraries.

Docker is a platform for developers and sysadmins to develop, deploy, and run applications with containers. The use of Linux containers to deploy applications is called containerization. Containers are not new, but their use for easily deploying applications is.

### Images and Container

A container is launched by running an image. An image is an executable package that includes everything needed to run an application--the code, a runtime, libraries, environment variables, and configuration files.

A container is a runtime instance of an image--what the image becomes in memory when executed (that is, an image with state, or a user process). You can see a list of your running containers with the command **``` docker ps```** just as you would in Linux.

---

### Testing Docker
Run  **```docker --version```** and ensure that you have a supported version of Docker.

---

### Pulling your first image

Run **``` docker run hello-world```*** to download your first docker image. To check the downloaded images, type **```docker images```**.
If you get something like 

REPOSITORY | TAG | IMAGE ID | SIZE
------------ | ------------- | ------------- | -------------
```hello-world``` | ```latest``` | ```4ab4c602aa5e``` | ```1.84kB```

then you have successfully downloaded the hello-world image onto your computer.

---

### Running your first image
