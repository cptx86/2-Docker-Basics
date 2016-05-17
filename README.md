## 2   Docker Basics
### Installation of Docker on Your Test Computer System
[Install Docker Engine] https://docs.docker.com/engine/installation/
#### Update the Ubuntu 14.04 LTS OS and Install Docker
```
sudo apt-get update
sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
echo "deb https://apt.dockerproject.org/repo ubuntu-trusty main" > docker.list
sudo mv docker.list /etc/apt/sources.list.d/docker.list
sudo apt-get update
sudo apt-get install linux-image-extra-$(uname -r)
sudo apt-get install docker-engine
sudo service docker start
```
### Run Your First Container
#### Verify Docker is Installed and Working
```sudo docker run hello-world```
### You Just Launched Your First Container!
#### Run the hello-world Container Again
```sudo docker run hello-world```
#### List Images
```sudo docker images```
#### List All Containers
```sudo docker ps -a```
#### Remove Container by Container ID
```
sudo docker rm 3722c80e8a9c
sudo docker ps -a
```
#### Remove Containers by Container Name
```
sudo docker rm high_yalow
sudo docker ps -a
```
#### Remove Image by Image Name
```sudo docker rmi hello-world```
#### Run New Container and Show History of Image
```
sudo docker run hello-world
sudo docker history hello-world
```
#### List All Information Available on an Image or Container
```sudo docker inspect a3e5b6fb3fce```
### More About Containers
```
sudo docker run --name="hello-world" hello-world
sudo docker ps -a
```
#### Remove Container by Container Name
```sudo docker rm hello-world```
#### Display Help for Command Usage, Function, and Options
```sudo docker ps --help```
#### Open Docker Run Command Manual Page
```man docker-run```
#### Display System-Wide Docker Information
```sudo docker info```
#### Display the Docker Version
```sudo docker version```
#### Pull an Image from the Docker Hub Registry
```sudo docker pull ubuntu:14.04.3```
#### Run an Interactive Shell in a Container
```
sudo docker run -i -t ubuntu:14.04.3 /bin/bash
ps -ef
exit
sudo docker rm $(sudo docker ps -qa)
```
#### Run a Container in Detached Mode
```
sudo docker run -d -i ubuntu:14.04.3
sudo docker ps
sudo docker stop $(docker ps -qa)
sudo docker rm $(docker ps -qa)
```
### Review Basic Commands
```
sudo docker run hello-world
sudo docker images
sudo docker  ps -a
sudo docker  ps
sudo docker rm 3722c80e8a9c
sudo docker rm $(sudo docker ps -a -q)
sudo docker rmi hello-world
sudo docker history hello-world
sudo docker inspect b901d36b6f2f
sudo docker run --name="hello-world" hello-world
man docker-run
sudo docker info
sudo docker version
sudo docker pull ubuntu:14.04.3
sudo docker run -i -t ubuntu:14.04.3 /bin/bash
sudo docker run -d -i ubuntu:14.04.3
sudo docker stop $(sudo docker ps -qa)
sudo docker rm $(sudo docker ps -qa)
sudo docker rmi $(sudo docker images -qa)
```
### Where are Docker Images Stored?
```
sudo service docker stop
sudo cp -rp /var/lib/docker /usr/local
sudo rm -r /var/lib/docker
sudo ln -s /usr/local/docker /var/lib/docker
sudo service docker start
```
#### Modify Docker Daemon Startup Configuration File
```
sudo vi /etc/default/docker
sudo service docker restart
sudo cat /var/log/upstart/docker.log
```
#### List Storage Usage
```sudo du -sh /usr/local/docker```
### Docker Hub
#### Search for Public Images on Docker Hub
```
sudo docker search hello-world
sudo docker pull hello-world
```
#### Create a Docker Hub Account and Repository
[Docker Hub] https://hub.docker.com/register/
#### Add User to the Docker Group
```sudo gpasswd -a `id -un` docker```
#### Login and Push an Image to Docker Hub
```
docker images | grep hello-world
docker login
docker tag hello-world cptx86/hello-world:latest
docker push cptx86/hello-world:latest
```
#### Additional Reading about Docker Hub
[Welcome to Docker Hub] https://docs.docker.com/docker-hub/

