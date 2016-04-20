## 2   Docker Basics
### Select a Test Computer System to Learn Docker
```
uname -r
```
### Installation of Docker on Your Test Computer System
#### Update the Ubuntu 14.04 LTS OS and Install Docker
```
sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
echo "deb https://apt.dockerproject.org/repo ubuntu-trusty main" > docker.list
sudo mv docker.list /etc/apt/sources.list.d/docker.list
sudo apt-get update
sudo apt-get install docker-engine
sudo service docker start
```
## Appendix A: Test Computer System Configuration
#### Installation of OpenSSH Server
sudo apt-get install openssh-server
#### Create SSH Keys
ssh-keygen -t rsa
#### Install and Connect to Test Computer System with Putty
http://support.hostgator.com/articles/specialized-help/technical/ssh-keying-through-putty-on-windows-or-linux
#### Static IP
```
sudo vi /etc/network/interfaces
sudo vi /etc/hosts
sudo reboot
```




