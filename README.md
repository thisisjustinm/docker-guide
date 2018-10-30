## Docker Guide 

This is a temporary guide to get you guys started on Docker. This, by **NO** means is a complete guide. Read the original documentation at
[Docker Documentation](https://docs.docker.com/get-started/).

### Contents

* [Introduction](/#introduction)
* [Testing ](/README.md/#Introduction)

### Introduction
Docker provides a way to run applications securely isolated in a container, packaged with all its dependencies and libraries.
It is a platform for developers and sysadmins to develop, deploy, and run applications with containers. The use of Linux containers to deploy applications is called containerization. Containers are not new, but their use for easily deploying applications is.
It makes use of container to make it easier to create, deploy, and run applications.

A [*container*](https://docs.docker.com/get-started/part2/) is launched by running an *image*. An image is an executable package that includes everything needed to run an application--the code, a runtime, libraries, environment variables, and configuration files.

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

then you have successfully downloaded the [hello-world](https://hub.docker.com/_/hello-world/) image onto your computer.

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

---

### Playing with [Alpine](https://alpinelinux.org/)

Try out the following commands to get an overview of Docker.:

* **```docker pull alpine:latest```** : This pull fetches latest alpine images and saves it to your system.
* **```docker run alpine echo "Hello, World" ```** : Runs the alpine container(and then exits it).
* **```docker ps -a```** : See the list of containers we have run.
* **```docker run -it alpine sh```** : This opens an interactive shell using the flag **-it**, where you can type more than one command. To exit, type **```exit```**.
* **```docker stop <container_id>```** : To stop a running container.
* **```docker rm <container_id>```** : To remove the stopped container.
* **```docker container prune ```** : To remove all stopped containers.

---

### Webapps with Docker

In this example, I will be using a [web application](https://hub.docker.com/r/thisisjustinm/webcat/) already available on the docker-hub. Pull the image via **```docker pull thisisjustinm/webcat```**. Once you have downloaded, run it using the command **```docker run -d -P --name webcat thisisjustinm/webcat```**. The flag ```-d``` is used to run the container detached and ```-P``` is used to run the web application on a random port. The flag ```--name ``` is used to give a name to the container.

Once you run it, you may get a hash like ```2044d71021a422044d710.....0afff6435f```. This means the container is running. To view/publish at which port the container is running, use the command **```docker port webcat```**. This publishes the port, which we can access in our browser.

To get the IP at which the machine is running use the command **```docker-machine ip default ```** . You may get something like: ```192.68.99.100``` (example)

Open the browser and type in the url as: ```<your_machine_ip>:<port>```. e.g. 192.168.99.100:4000

Now, we have sucessfully run a web application with Docker.

---

### Creating Docker Images

A Dockerfile is a simple text file that containes a list of commands that Docker client calls while creating an image. Following are the important Dockerfile instructions to remember:
1. **FROM** : The FROM instruction initializes a new build stage and sets the Base Image for subsequent instructions. As such, a valid Dockerfile must start with a FROM instruction. 
e.g. FROM alpine:latest

2. **RUN** : The RUN instruction will execute any commands in a new layer on top of the current image and commit the results. The resulting committed image will be used for the next step in the Dockerfile. 
e.g. RUN apk update

3. **COPY** : The COPY instruction copies new files or directories from <src> and adds them to the filesystem of the container at the path <dest>. 
 e.g. COPY index.html /usr/share/nginx/
 
4. **CMD** : Used to run certain specified shell commands.The main purpose of a CMD is to provide defaults for an executing container. e.g. CMD \["figlet","hello"\]

5. **EXPOSE** : The EXPOSE instruction informs Docker that the container listens on the specified network ports at runtime. You can specify whether the port listens on TCP or UDP, and the default is TCP if the protocol is not specified. 
e.g. EXPOSE 3001

Read more about these [here](https://docs.docker.com/engine/reference/builder/).

---

### Creating your first Dockerfile

Create a Dockerfile, open it any text editor and add the following:

FROM alpine:latest <br>
RUN apk add figlet <br>
CMD \["figlet", "Your name"\]<br>

Build this Dockerfile using the command **``` docker build -t yourusername/imagename . ```**
Here, yourname is you username on [Docker-Hub](https://hub.docker.com) and imagename is the name that you give to the image. The dot is thelocation of the file i.e. the current directory e.g. thisisjustinm/webcat . To run this image, type in the command as **```docker run -d yourusername/imagename```**.

Once you have created the image, you can push it to the hub, so that others can access. To do so, login with command **```docker login```** and login with your docker hub username and password. Once logged in, you can push the image via, **```docker push yourusername/imagename```**. 

Please read more about this [here](https://docs.docker.com/get-started/part2/#dockerfile).

---

### Creating your first webapp

1. Create a webpage ```index.html```. An example code can be found [here](https://pastebin.com/wFzTnCAw).
2. Create a Docker file <br>
FROM nginx:latest<br>
COPY index.html /usr/share/nginx/html<br>
EXPOSE 3000<br>
3. Build the Dockerfile: **```docker build -t yourusername/imagename```** and push it to Docker Hub.
4. Run the container, as explained above.

----

### Some handy shortcuts

1. List all containers : **```docker ps -aq```**
2. Stop all running containers : **```docker stop $(docker ps -aq)```**
3. Remove all stopped containers : **```docker rm $(docker ps -aq)```**
