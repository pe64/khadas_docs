title: Install Docker
---

This tutorial is about how to install Docker on Ubuntu for Khadas VIMs/Edge.

### Preperations
* Ubuntu `V180531` or newer

### Install some essential packages
```
khadas@Khadas:~$ sudo apt-get update
khadas@Khadas:~$ sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
khadas@Khadas:~$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```
### Add Docker source
```
khadas@Khadas:~$ sudo add-apt-repository \
			"deb [arch=arm64] https://download.docker.com/linux/ubuntu \
			$(lsb_release -cs) \
			stable"
```
### Install Docker
```
khadas@Khadas:~$ sudo apt-get update
khadas@Khadas:~$ sudo apt-get install docker-ce=18.03.1~ce-0~ubuntu
```

### Start Docker
```
khadas@Khadas:~$ sudo systemctl enable docker
khadas@Khadas:~$ sudo systemctl start docker
```

### Add Docker group
```
khadas@Khadas:~$ sudo groupadd docker
khadas@Khadas:~$ sudo usermod -aG docker $USER
```

*NOTE: You need to logout or reboot your system.*

### Check Docker
```
khadas@Khadas:~$ docker run hello-world
```

If you see the following messages mean that Docker is setup OK.
```
khadas@Khadas:~$ docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
255483503861: Pull complete 
Digest: sha256:4b8ff392a12ed9ea17784bd3c9a8b1fa3299cac44aca35a85c90c5e3c7afacdc
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (arm64v8)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/engine/userguide/
```

### See also
[Get Docker CE for Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/)
