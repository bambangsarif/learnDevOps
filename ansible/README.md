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

