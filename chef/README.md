This is the folder for chef training

1. start with spinning up a new workstation using vagrant

2. install chef jdk (use wget to chef.io)

3. configure chef 'chef configure'

4. create cookbook:'mkdir cookbook, cd cookbook, chef generate cookbook my_cookbook'

5. create the first recipe (look at the chef-demo git)

6. edit the first recipe (cookbooks/my_cookbook/recipes/default.rb) to use a cookbook 'apt

7. download cookbook 'apt'. There's two ways 1) initiate berks 2) berks vendor
   berks init, berks install --> it will create ~/.bershelf/cookbooks/apt-x.x.x folder
   berks vendor will create berks-cookbooks folder that contain 'apt' and our cookbook. mv the apt folder to the cookbook folder
   with this ~/cookbook will contain apt and my_cookbook folders. This will work with our knife configuration where our cookbook path
   is ~/cookbook
   
8. try to run it locally!
   run chef client 'sudo chef-client -z --runlist "recipe[my_cookbook]"'
   try the new nginx engine 'curl localhost'
