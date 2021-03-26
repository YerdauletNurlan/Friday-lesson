### Vagrant ###
#### installing vagrant ####
`sudo apt install virtualbox`

`curl -O https://releases.hashicorp.com/vagrant/2.2.6/vagrant_2.2.6_x86_64.deb`

`sudo apt install ./vagrant_2.2.6_x86_64.deb`

#### creating hosts with vagrant ####
##### create directory where vagrant will be #####
`mkdir vagrant`

`cd vagrant` 
##### add vagrantfile #####
`vagrant init`
##### change Vagrantfile #####
`nano Vagrantfile` 
##### run vagrant #####
`vagrant up`
##### go into host1 #####
`vagrant ssh host1`
##### stop vagrant #####
`vagrant halt`



### HOST1 ###
#### Installing haproxy ####
`sudo add-apt-repository ppa:vbernat/haproxy-1.8`

`sudo apt-get update`

`sudo apt-get install haproxy`
##### modify haproxy config file #####
`sudo nano /etc/haproxy/haproxy.cfg`
##### if you write config file correctly haproxy will work #####
`sudo systemctl status haproxy`  
##### restart haproxy after updating config file #####
`sudo systemctl restart haproxy`
##### install keepalived #####
`sudo apt install keepalived`
##### enable ip forwarding #####
`sed -i 's/#net.ipv4.ip_forward=1/net.ipv4.ip_forward=1/' /etc/sysctl.conf`

`echo "net.ipv4.ip_nonlocal_bind = 1" >> /etc/sysctl.conf`

`sysctl -p`
##### modify keepalived config file #####
`sudo nano /etc/keepalived/keepalived.conf`
##### run keepalived #####
`sudo systemctl start keepalived`
##### check keepalived status #####
`sudo systemctl status keepalived`



### HOST2 ###
#### Installing docker ####
`sudo apt-get update`

`sudo apt install apt-transport-https ca-certificates curl software-properties-common`

`curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`

`sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"`

`sudo apt-get update`

`sudo apt-get install docker-ce`
##### check docker service status #####
`sudo systemctl status docker`
##### add docker to user to don't write sudo constantly #####
`sudo usermod -aG docker ${USER}`

`su - ${USER}`

`id -nG`
##### run docker container #####
`docker run -it --rm -d -p 8080:80 --name web nginx`

`docker run -it --rm -d -p 8081:80 --name web2 nginx`
##### check container #####
`docker ps`
##### add html file into container web #####
`docker cp index.html web:/usr/share/nginx/html/index.html`

`docker cp index2.html web2:/usr/share/nginx/html/index.html`


### HOST3 ###
#### Installing haproxy ####
`sudo add-apt-repository ppa:vbernat/haproxy-1.8`

`sudo apt-get update`

`sudo apt-get install haproxy`
##### modify haproxy config file #####
`sudo nano /etc/haproxy/haproxy.cfg`
##### if you write config file correctly haproxy will work #####
`sudo systemctl status haproxy`  
##### restart haproxy after updating config file #####
`sudo systemctl restart haproxy`
##### install keepalived #####
`sudo apt install keepalived`
##### enable ip forwarding #####
`sed -i 's/#net.ipv4.ip_forward=1/net.ipv4.ip_forward=1/' /etc/sysctl.conf`

`echo "net.ipv4.ip_nonlocal_bind = 1" >> /etc/sysctl.conf`

`sysctl -p`
##### modify keepalived config file #####
`sudo nano /etc/keepalived/keepalived.conf`
##### run keepalived #####
`sudo systemctl start keepalived`
##### check keepalived status #####
`sudo systemctl status keepalived`


https://github.com/YerdauletNurlan/Friday-lesson
