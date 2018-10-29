## Docker Guide 

Docker provides a way to run applications securely isolated in a container, packaged with all its dependencies and libraries.

Docker is a platform for developers and sysadmins to develop, deploy, and run applications with containers. The use of Linux containers to deploy applications is called containerization. Containers are not new, but their use for easily deploying applications is.

Docker makes use of container to make it easier to create, deploy, and run applications.

A *container* is launched by running an *image*. An image is an executable package that includes everything needed to run an application--the code, a runtime, libraries, environment variables, and configuration files.

A container is a runtime instance of an image--what the image becomes in memory when executed (that is, an image with state, or a user process). You can see a list of your running containers with the command **``` docker ps```** just as you would in Linux.

---

### Testing Docker
Run  **```docker --version```** and ensure that you have a supported version of Docker.

---

### Pulling your first image

Run **``` docker run hello-world```** to download your first docker image. To check the downloaded images, type **```docker images```**.
If you get something like 

REPOSITORY | TAG | IMAGE ID | SIZE
------------ | ------------- | ------------- | -------------
```hello-world``` | ```latest``` | ```4ab4c602aa5e``` | ```1.84kB```

then you have successfully downloaded the hello-world image onto your computer.

---

### Running your first image
To run the hello-world image, type in the command **```docker run hello-world```**

Example output:

```
Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
  
```
### Playing with [Alpine](https://alpinelinux.org/)

Try out the following commands:

* **```docker pull alpine:latest```** : This pull fetches latest alpine images and saves it to your system.
* **```docker run alpine echo "Hello, World" ```** : Runs the alpine container(and then exits it).
* **```docker ps -a```** : See the list of containers we have run.
* **```docker run -it alpine sh```** : This opens an interactive shell using the flag **-it**, where you can type more than one command. To exit, type **```exit```**.
* **```docker stop <container_id>```** : To stop a running container.
* **```docker rm <container_id>```** : To remove the stopped container.
* **```docker container ```** : To remove all stopped containers.

### Webapps with Docker

In this example, I will be using a web application already available on the docker-hub. Pull the image via **```docker pull thisisjustinm/webcat```**. Once you have downloaded, run it using the command **```docker run -d -P --name webcat thisisjustinm/webcat```**. The flag ```-d``` is used to run the container detached and ```-P``` is used to run the web application on a random port. The flag ```--name ``` is used to give a name to the container.

Once you run it, you may get a hash like ```2044d71021a42dc6c06dedcc393f70a3f7c2a0b10435a145c639aa30afff6435f```. This means the container is running. To view/publish at which port the container is running, use the command **```docker port webcat```**. This publishes the port, which we can access in our browser.

To get the IP at which the machine is running use the command **```docker-machine ip default ```** . You may get something like: 
> 192.68.99.100 (example)

Open the browser and type in the url as:
> <your_machine_ip>:<port>

Now, we have sucessfully run a web application with Docker.

### Docker Image
