## 2   Docker Basics
### Select a Test Computer System to Learn Docker
```
uname -r
```
### Installation of Docker on Your Test Computer System
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
```
sudo docker run hello-world
```

## Appendix A: Test Computer System Configuration
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






