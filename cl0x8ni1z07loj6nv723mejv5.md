## Here's how Docker makes your life easier

Have you experienced this, when you created an application it works perfectly on your machine 😎, so you share your application with another developer you said to run this application on their machine and give me some feedback, unfortunately, he says bruh your application is not working on my machine 🙁, then you will say the popular word **"It works on my machine"**, but why the application is **not working** on his machine? 🤔 

### What is Docker?

**Docker** is a tool and it is also a company <a target = "_blank" href= "https://www.docker.com"> Docker inc</a> 
it is a **container platform** that allows us to build, run, test, and deploy applications rapidly it can run on multiple operating machines, servers, databases, and many more.

### Why use Docker?

Because by using docker we can run the software on any environment, might be it Linux, windows, ubuntu,  mac by using docker we have full control of our product, it is easy for developers to run and test,
we can ship the application from the local system into production quickly 🚀, docker is helpful in the **entire workflow** of **software development**, but it is particularly used in the **deployment phase**
![20cmt5jrcl0m61hh7ri8.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1647600956845/QbWlOgfsV.png)


### How does it works?

containerization and virtualization

![Docker-containers-are-not-lightweight-virtual-machines.webp](https://cdn.hashnode.com/res/hashnode/image/upload/v1647601195702/KhYG8CEQh.webp)

Any **compute** mean a server, machine want to have these essentials **[CPU, RAM, NETWORK]** 
let's see how **VM** works here the physical server means it uses hardware resources from the local computer, server, cloud. and the **hypervisor** allocates resources for the running virtual machines, here the problem is, it requires separate guest os and it splits the host resources for every new VM

We can say containers are lightweight VM's, it does not want to have a separate **operating system** to run any applications, we can say containers are just a bunch of normal processes, works with host kernel, technically saying even kernel doesn't know containers are running on the top of his head. containers are executed process which doesn't communicate with the outside world, it is handled by **cgropus and namespaces**.

### Docker setup

**Installation**

![setup.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1647605128486/5kbtoOm8b.PNG)

For download and installation refer <a target = "_blank" href= "https://docs.docker.com/get-docker/"> docs.docker.com</a> 

### Docker architecture


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1647604695065/LQgv-MeNP.png)

Docker architecture is a **client-server** architecture

#### Docker daemon

Docker **daemon** is like the heart of docker engine, it talks to the runc, runc responsibility is to start and stop the container, and in the daemon we have containerd which control's the runc, what if suddenly daemon shut down 🤯, the container data and state will be lost, this is not want to happen so we use a shim for this, shim task is to after the runc responsibility is over, runc handles the next step to shim. so even the daemon is not available the shim will run the containers 😎.

#### Docker client

The initial step to **communicate** with the daemon is to use commands which are understood by the docker client we give these commands in the **docker(CLI)** command-line interface then these commands send as a request to **rest APIs**, these requests act as a **medium** if we want to communicate with docker daemon if all goes well then we get a response from the server.

### Docker registries

A registry is an online repository to store images, Docker has its own registry called docker hub, there are some other registries out there such as AWS and google's own container image registry.

### Docker file

To create an image first we want to have a docker file, the file basically having all the **instructions** to perform a particular task which we want to design for our own needs, let's see how we can create a **docker file**
 
let's see what are the steps required to create a docker file. 
    
#### Example

* Create a file named 'Dockerfile'
       touch dockerfile

* Open dockerfile by using visual editor type this command
       vi dockerfile

* In that enter this 

        FROM ubuntu:16.04
        MAINTAINER Krishnamohan Yerrabilli <mailtomohanse@gmail.com>
        RUN apt-get update
        CMD ["echo","Hello-world"]

* After entering this press Esc and press ':x' press enter to exit the editor 

* Now you have dockerfile, time to build the image, to create image enter the below command

       docker build -t demoimage .

* Similar to this happen **automatically**

       1 [internal] load build definition from Dockerfileoimage 
       1 sha256:5e87f2bbef72670603317ea4da534c6f0c5bcb1e9e72f4ab5d3c14393458179
       1 transferring dockerfile: 76B 0.0s done
       1 DONE 0.1s

       2 [internal] load .dockerignore
       2 sha256:957ec0d151d5fff30381105855e273ea5ac5a0ee60f3f3dc4f723a1c610b0fd3
       2 transferring context: 2B done
       2 DONE 0.0s

       3 [internal] load metadata for docker.io/library/ubuntu:16.04
       3 sha256:8dff2c23d5907ba94f7c361d130cc16c98c9f3ad54aa1c116e150ea96355a327
       3 DONE 9.7s

       4 [1/2] FROM docker.io/library
       /ubuntu:16.04@sha256:0f71fa8d4d2d4292c3c617fda2b36f6dabe5c8b6e34c3dc5b0d17d4e704bd39c
       4 sha256:5d4d8795788a689b146c388dd2616e1074d7541ae11e7119f42369b4e3dbd2e2
       4 CACHED

       5 [2/2] RUN echo Hello-world
       5 sha256:be7119c83c6888ea2cc512a1c27c885448ea951b6092a78e49765a230c724229
       5 0.953 Hello-world
       5 DONE 1.0s

       6 exporting to image
       6 sha256:e8c613e07b0b7ff33893b694f7759a10d42e180f2b4dc349fb57dc6b71dcab00
       6 exporting layers
       6 exporting layers 0.1s done
       6 writing image sha256:064f60eb716505480a4c7b17d6f4bca2b015a3ada3704439ea1c6d84c83bb674 
       0.0s done
       6 naming to docker.io/library/demoimage done
       6 DONE 0.2s

       Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them

Congratulations you created your first image 🥳

* Command to see locally existing docker images

       docker images

### Docker image

Docker image is used to define docker container, now this image is very portable
to carry means whoever using **docker desktop** for that particular os can run this 
image from anywhere, images are portable, you can carry these images to anywhere
they are like an instruction manual, the image can be stored locally on your system or it can be
upload to the remote repo <a target = "_blank" href= "https://hub.docker.com"> hub.docker.com</a>

* Command to run the image

        docker run demoimage

* If all goes well, this will be the output
        Hello-world

#### Basic commands

        docker ps (shows containers if they are currently running)
        docker rmi 'imagename' (remove the image)
        docker images -q (shows all images ids)
        docker stop 'containerid' (stop the running container)
        docker ps -a (shows all stopped containers)

### Docker components

![components.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1647613081687/pzgydLsJQ.png)

Let's see how each **component** of docker works together actually, these images are built in layers, previously we created an image by using 4 lines of commands, to be precise each instruction (each line is a layer), each layer built on the top of the **previous layer**. each layer has its own hash id these ids are generated by the docker engine 

### Pulling image

* This image does not have locally stored so it's pulling from the docker hub

        DELL@DESKTOP-H460TGR MINGW64 ~/mohan
        $ docker run hello-world
       Unable to find image 'hello-world:latest' locally
        latest: Pulling from library/hello-world
        2db29710123e: Already exists
       Digest: sha256:f861ba8563637d693e3043069b0a4ebf3d92c2e865b541379f6a6b8164b7c8bb
       Status: Downloaded newer image for hello-world:latest

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

* To try something more ambitious, you can run an Ubuntu container with

       $ docker run -it ubuntu bash

* For more examples and ideas, visit:
       https://docs.docker.com/get-started/

### Containers

![alexandre-lallemand-QTfIXdE2ozw-unsplash(1).jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1647648573075/L2kyNF6T6.jpg)


Containers are the instance of an image, containers are handled by shim, containers are also called as
lightweight VM's, containers provide a high level of security because it does not talk to host operating 
system and a container does not know what happens outside of the container, containers have their own
operating system to run, 

We saw `From ubuntu:16.04` this means all image's that we creating want to
have a base operating system in this case it is `ubuntu:16.04` on the top of this os, we can give any functionality depending on dev to dev which can be designed for their own needs. one of the great features
is we can set up an open-source environment in seconds, containers are handy when we are participating in
hackathons and stuff.
 
### What's next?

What if you run 100 to 1000's containers **simultaneously**, means you deployed your application(v1) on many servers now you want to release v2 of your app, what do you do now? do you stop the whole containers and restart it? how do you monitor all containers? this is gonna be a tedious task for the operations team

This is where **orchestration engines** comes into picture, these tools manage container deployment, scaling and de-scaling, and many other operations, one of the most popular orchestration engine is **Kubernetes**, it is launched by Google, but now it's currently maintained by CNCF(Cloud Native Computing Foundation), That's another story. 😄


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1647650839154/ehA0rqTdE.png)



<p>
Thank you for reading my blog. Feel free to connect on <a target = "_blank" href= "https://www.linkedin.com/in/krishnamohanyerrabilli"> LinkedIn </a> or <a target = "_blank" href= "https://www.twitter.com/Kmohan_y">Twitter</a>. 😊
