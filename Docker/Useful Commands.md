1. **docker exec -it [containerName\ID] /bin/bash** similar to attach, but for specific situation where the container is in /bin/bash mode.

2. **docker rm $(docker ps -a -q)** remove all containers;  

3. **docker rmi $(docker images -q)** remove all images;  

4. **docker system prune** will remove 1. all stopped containers 2. all volumes not used by any container 3. all images without any container associated to them

5. **docker {container,image,volume,network} prune** will remove unused instances of just one type of object.

6. **docker system df** shows the general information of your images, containers and local volumes.

7. **docker system events** shows all the events, you can add options like --since, --filter, --until, --format. Then if you open another terminal window and do something on your docker, in the previous window, it will show real time docker events.

8. `--cap-add` and `--cap-drop` can give or remove the capabilities of your containers.  

9. Super Privileged container
We can run a privileged container by using --privileged flag to add all capabilities to the container. An example:   
    
    
       docker run -it --name rhel-tools --privileged                      \
            --ipc=host --net=host --pid=host -e HOST=/host                \
            -e NAME=rhel-tools -e IMAGE=rhel7/rhel-tools                  \
            -v /run:/run -v /var/log:/var/log                             \
            -v /etc/localtime:/etc/localtime -v /:/host rhel7/rhel-tools
 
The --ipc=host, --net=host, and --pid=host flags turn off the ipc, net, and pid namespaces inside the container. This means that the processes within the container see the same network and process table, as well as share any IPCs with the host processes.
 
-e flag sets environment variables inside the container. For example, -e HOST=/host: Sets the location of the host filesystem within the container (in other words, where / from the host is mounted). You can append $HOST to any file name so a command you run accesses that file on the host instead of within the container. For example, from within the container, $HOST/etc/passwd accesses the /etc/passwd file on the host.
-v flag is used to mount file system from host to container. For example, -v /run:/run option mounts the /run directory from the host on the /run directory inside the container. This allows processes within the container to talk to the host’s dbus service and talk directly to the systemd service. Processes within the container can even communicate with the docker daemon.

10. Run containers with capabilities
With --cap-add flag, you can add capabilities to the container. Possible Linux capabilities could be found here.  

11. Disable security related technologies
It's better to keep the security related technologies docker supports like apparmor or seccomp, so we may want to prevent customers disabling them or changing them. An example would be:

        docker run --rm -it --security-opt seccomp=unconfined debian:jessie sh
