#Vagrant
#installing vagrant
sudo apt install virtualbox
curl -O https://releases.hashicorp.com/vagrant/2.2.6/vagrant_2.2.6_x86_64.deb
sudo apt install ./vagrant_2.2.6_x86_64.deb

#### creating hosts with vagrant ####
mkdir vagrant #create directory where vagrant will be
cd vagrant 
vagrant init #add vagrantfile 
nano Vagrantfile #change Vagrantfile
vagrant up #run vagrant
vagrant ssh host1 #go into host1
vagrant halt #stop vagrant



#HOST1
#Installing haproxy
sudo add-apt-repository ppa:vbernat/haproxy-1.8
sudo apt-get update
sudo apt-get install haproxy
nano /etc/haproxy/haproxy.cfg #open haproxy config file
sudo systemctl status haproxy #if you write config file correctly haproxy will work 
sudo systemctl restart haproxy #restart haproxy after updating config file


#HOST2
#Installing docker
sudo apt update
sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
sudo apt update
sudo apt install docker-ce

sudo systemctl status docker #check docker service status
sudo usermod -aG docker ${USER}
su - ${USER}
id -nG

docker run -it --rm -d -p 8080:80 --name web nginx #run docker container
docker ps #check container
docker cp index.html web:/usr/share/nginx/html #add html file into container web






https://github.com/YerdauletNurlan/Friday-lesson
