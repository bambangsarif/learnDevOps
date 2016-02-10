This README is for chef server experiment

1. In order to work, chef need a fully qualified domain name. We can 'fake' it by putting the 
information on the /etc/hosts file. We need to put it on the chef server, node and workstation.
To make it easy, make a hosts file on vagrant provisiong folder. After vagrant up, we can copy 
the hosts file into /etc/hosts file.
For our experiment, the hosts file is as follow

192.168.56.253 chef.example.com chef
192.168.56.252 workstation.example.com workstation
192.168.56.3 node.example.com node

