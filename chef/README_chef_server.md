This README is for chef server experiment

NOTE:
we need to have server, workstation and node. workstations are machines where we can author cookbooks. nodes are client

1. In order to work, chef need a fully qualified domain name. We can 'fake' it by putting the 
information on the /etc/hosts file. We need to put it on the chef server, node and workstation.
To make it easy, make a hosts file on vagrant provisiong folder. After vagrant up, we can copy 
the hosts file into /etc/hosts file.
For our experiment, the hosts file is as follow

192.168.56.253 chef.example.com chef
192.168.56.252 workstation.example.com workstation
192.168.56.3 node.example.com node

2. install chef server

3. configure chef server 'chef-server-ctl reconfigure'
   option: we can also install the web GUI, if the number of nodes is <25 using the following command
   chef-server-ctl install opscode-manage
   chef-server-ctl reconfigure
   opscode-manage-ctl reconfigure

4. create admin user and organization
   chef-server-ctl user-create admin "First name Administrator" "last name" admin@example.com <PASSWD> -f admin.pem
   chef-server-ctl org-create learndevops "Learn DevOps Course" --association_user admin -f org.pem

5. copy the generated .pem file to the workstation root folder

6. create knife.rb in .chef folder (copy from demo) o

7. fetch the knife 'knife ssl fetch', check it 'knife client list'

8. bootstrap a new node 'knife bootstrap node.example.com -N node -x vagrant --sudo
   note: if we dont use the fqdn node.example.com, we need to provide the node id

9. prepare the cookbook. upload to server. 'knife cookbook upload apt' 'knife cookbook upload my_cookbook'

10. prepare the node run-list "knife node run_list set node 'recipe[my_cookbook]'"

11. run the chef client on node "ssh node 'sudo chef-client'"

12. assigning role. copy the demo webserver role .json file. Also use copy attributes templates and recipes folder to my_cookbook

13. modify the version part in metadata. otherwise the change will not be taken by the server

14. upload the webserver role. update the run_list of node 'knife role from file <JSON FILE>' 'knife node run_list set node "role[webserver]"'

15. push the changes to the client by running chef-client on node "ssh node 'sudo chef-client'". Otherwise, we need to wait for 30 minutes for the change to be pulled. We will see that the node is using [role[webserver]]
