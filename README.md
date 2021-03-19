### Vagrant ###
#### installing vagrant ####
<sudo apt install virtualbox >
curl -O https://releases.hashicorp.com/vagrant/2.2.6/vagrant_2.2.6_x86_64.deb
sudo apt install ./vagrant_2.2.6_x86_64.deb

#### creating hosts with vagrant ####
##### create directory where vagrant will be #####
mkdir vagrant 
cd vagrant 
##### add vagrantfile #####
vagrant init  
##### change Vagrantfile #####
nano Vagrantfile 
##### run vagrant #####
vagrant up
##### go into host1 #####
vagrant ssh host1
##### stop vagrant #####
vagrant halt 



### HOST1 ###
#### Installing haproxy ####
sudo add-apt-repository ppa:vbernat/haproxy-1.8
sudo apt-get update
sudo apt-get install haproxy
##### open haproxy config file #####
nano /etc/haproxy/haproxy.cfg
##### if you write config file correctly haproxy will work #####
sudo systemctl status haproxy  
##### restart haproxy after updating config file #####
sudo systemctl restart haproxy


### HOST2 ###
#### Installing docker ####
sudo apt update
sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
sudo apt update
sudo apt install docker-ce

##### check docker service status #####
sudo systemctl status docker
##### add docker to user to don't write sudo constantly #####
sudo usermod -aG docker ${USER}
su - ${USER}
id -nG
##### run docker container #####
docker run -it --rm -d -p 8080:80 --name web nginx 
##### check container #####
docker ps
##### add html file into container web #####
docker cp index.html web:/usr/share/nginx/html






https://github.com/YerdauletNurlan/Friday-lesson
