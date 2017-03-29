### Firewall  
1. Check the status of firewall  

       systemctl status firewalld  
2. Disable firewall
        
       systemctl disable firewalld  
3. Stop firewall  

       systemctl stop firewalld  
4. Enable firewall  

       systemctl enable firewalld  

### Network
1. Assign an IP address to your VM: 

       sudo dhclient -v -v -r  then  sudo dhclient
