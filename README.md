## 2   Docker Basics
### Select a Test Computer System to Learn Docker
```uname -r```
### Installation of Docker on Your Test Computer System
[Install Docker Engine] https://docs.docker.com/engine/installation/
#### Update the Ubuntu 14.04 LTS OS and Install Docker
```
sudo apt-get update
sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
echo "deb https://apt.dockerproject.org/repo ubuntu-trusty main" > docker.list
sudo mv docker.list /etc/apt/sources.list.d/docker.list
sudo apt-get update
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
#### Remove Container by Container ID and List All Container
```
sudo docker rm 3722c80e8a9c
sudo docker ps -a
sudo docker rm boring_saha
sudo docker ps -a
```
#### List Images
```sudo docker images```
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
### Docker Security
#### Docker Trusted Registry 
[Docker Trusted Registry] https://docs.docker.com/docker-hub/official_repos/
#### Setup Docker to Run Without Requiring sudo
```sudo gpasswd -a `id -un` docker```
```
docker run hello-world
sudo service docker stop
sudo service docker start
sudo service docker restart
```
#### Modify Docker Daemon Configuration File with Log Level
```sudo vi /etc/default/docker```
```
DOCKER_OPTS="\
      --graph=/usr/local/docker \
      --dns 192.168.1.202 \
      --dns 8.8.8.8 \
      --dns 8.8.4.4 \
      --log-level error \
      "
```
```
sudo service docker restart
sudo cat /var/log/upstart/docker.log
```
#### Restrict Containers 'Linux Capabilities'
```docker run --help```
#### Seccomp Security Profiles for Docker
[Seccomp security profiles for Docker] https://github.com/docker/docker/blob/master/docs/security/seccomp.md
#### Encrypt Private Data Directory
[eCryptfs] https://help.ubuntu.com/12.04/serverguide/ecryptfs.html
#### Virtual Private Networking (VPN)
[OpenVPN] https://help.ubuntu.com/lts/serverguide/openvpn.html


#### Additional Reading about Securing Docker in a Linux System
[Docker Security] http://docs.docker.com/articles/security
https://docs.docker.com/engine/security/security/
[Docker Gets Serious About Security] http://www.eweek.com/security/docker-gets-serious-about-security.html
[Cross-Site Scripting (XSS)] https://www.owasp.org/index.php/Cross-site_Scripting_%28XSS%29

Docker Bench for Security is a script that checks for dozens of common best-practices around deploying Docker containers in production:
https://github.com/docker/docker-bench-security
Ubuntu Security
https://help.ubuntu.com/community/Security
Ubuntu security notices
www.ubuntu.com/usn/
Linux Kernel Security (SELinux vs AppArmor vs Grsecurity)
http://www.cyberciti.biz/tips/selinux-vs-apparmor-vs-grsecurity.html
OpenSSL
https://help.ubuntu.com/community/OpenSSL
Center for Internet Security Docker 1.6 Benchmark v1.0.0
https://benchmarks.cisecurity.org/downloads/show-single/index.cfm?file=docker16.100
Subscribing to ubuntu-security-announce
https://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce
Let’s Encrypt is a new Certificate Authority
https://letsencrypt.org/








## Appendix A: Test Computer System Configuration####
#### Installation of OpenSSH Server
sudo apt-get install openssh-server
#### Create SSH Keys
ssh-keygen -t rsa
#### Install and Connect to Test Computer System with Putty
http://support.hostgator.com/articles/specialized-help/technical/ssh-keying-through-putty-on-windows-or-linux
#### Static IP
#### Change DHCP to Static IP
```
sudo vi /etc/network/interfaces
sudo vi /etc/hosts
sudo reboot
```
#### Additional Reading about Networking
[Ubuntu Networking] https://help.ubuntu.com/lts/serverguide/networking.html
#### DNS
#### Installation of DNS
```
sudo apt-get update
sudo apt-get install bind9 bind9-doc bind9utils
```
#### Configure DNS
```
sudo vi /etc/bind/named.conf.options
sudo service bind9 restart
```
#### Create Primary Master for Domain
```
sudo vi /etc/bind/named.conf.local
sudo cp /etc/bind/db.local  /etc/bind/db.cptx86.com
sudo vi /etc/bind/db.cptx86.com
sudo service bind9 restart
```
#### Create Reverse DNS
```
sudo vi /etc/bind/named.conf.local
sudo cp /etc/bind/db.127 /etc/bind/db.192
sudo vi /etc/bind/db.192
```
#### Test Your DNS Lookup
```nslookup two.cptx86.com```
#### Test Reverse DNS Lookup
```nslookup 192.168.1.202```
#### Test Your DNS from Any Other Server on the Subnet
```dig @192.168.1.202 cptx86.com -t AXFR```
#### Security Through Obscurity
```
sudo vi /etc/bind/named.conf.local
sudo service bind9 restart
dig @192.168.1.202 cptx86.com -t AXFR
```
#### Modify Docker Daemon to Use DNS
```
sudo service docker restart
sudo vi /etc/hosts
```
#### Additional Reading about DNS
[Ubuntu Domain Name Service (DNS)] https://help.ubuntu.com/lts/serverguide/dns.html
#### NFS
#### Installation of NFS
```sudo apt-get install nfs-kernel-server```
#### Configure NFS
```
sudo vi /etc/exports
sudo exportfs -a
sudo service nfs-kernel-server start
showmount -e 192.168.1.202
```
#### Additional Reading about NFS
[Network File System] https://help.ubuntu.com/14.04/serverguide/network-file-system.html



