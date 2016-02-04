1. create two machines: 1 ansible, 1 webserver

Note: 

this happen with virtualbox version 4.3.12. I used this version because version 5 give an error related with the antivirus

when creating multiple vagrant up guests, make sure to use the same network address as the virtual box. For example, in the original slide, for ansible exercise, we created two hosts:
- webserver: 192.168.0.2
- ansible: 192.168.0.254

however, the virtual box host-only adapter is using 192.168.56.0/255
The above ip address setting will make vagrant up fail. Thus, we need to set the ip address of the above to machine to be in the same network as the virtual box. Hence
- webserver: 192.168.56.2
- ansible: 192.168.56.254

https://github.com/mitchellh/vagrant/issues/2392

2. create hosts file
   try to ping: ansible -i hosts -u root -m ping

3. create playbook: nginx.yml
   run it: ansible-playbook -i hosts -u root nginx.yml

4. modify the Vagrantfile to include nginx.yml ansible playbook

5. provisioning on AWS: install python-pip, boto library and awscli

6. create IAM AWS user

7. configure credential! use 'aws configure' and put the detail of the IAM user

8. allow the user to be able to import key-pair by attaching a policy towards the created user

9. import ssh key-pair using 'aws ect2 import-key-pair'
