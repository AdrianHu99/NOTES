1. **Seccomp**(secure computing mode) is used to restrict the syscalls available to a given process. Seccomp profiles are applied at container creation time, and can not be altered for running containers.

2. **AppArmor/SELinux** similar to **Seccomp**.

3. Docker has a [**CIS Benchmark**](https://benchmarks.cisecurity.org/tools2/docker/CIS_Docker_1.13.0_Benchmark_v1.0.0.pdf) which lets you run a container 
and it will check every best practices for you.   


        docker run -it --net host --pid host --cap-add audit_control \
        -e DOCKER_CONTENT_TRUST=$DOCKER_CONTENT_TRUST \
        -v /var/lib:/var/lib \
        -v /var/run/docker.sock:/var/run/docker.sock \
        -v /usr/lib/systemd:/usr/lib/systemd \
        -v /etc:/etc --label docker_bench_security \
        docker/docker-bench-security
        
4. 
