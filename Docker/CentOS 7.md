1. Create a CentOS 7 VM (64bit).
2. Make sure the internect is connected (`dhclient`).
3. You can choose to install [GUI](http://unix.stackexchange.com/questions/181503/how-to-install-desktop-environments-on-centos-7)
4. Update the existing packages
  `sudo yum update`  
5. Add the yum repo.
        
        sudo tee /etc/yum.repos.d/docker.repo <<-'EOF'  
        [dockerrepo]  
        name=Docker Repository  
        baseurl=https://yum.dockerproject.org/repo/main/centos/7/  
        enabled=1  
        gpgcheck=1  
        gpgkey=https://yum.dockerproject.org/gpg  
        EOF

6. Install Docker Engine.  
  `sudo yum install docker-engine`
  
7. Enable the service.  
  `sudo systemctl enable docker.service`
  
8. Start docker daemon.  
  `sudo systemctl start docker`
  
9. install docker compose.

        $ curl -L https://github.com/docker/compose/releases/download/1.8.0/docker-compose-`uname -s`-`uname -m` \
            >~/docker-compose  
        $ chmod +x ~/docker-compose  
        $ sudo mv ~/docker-compose /usr/local/bin/docker-compose  
  
