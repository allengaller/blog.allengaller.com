faxi@faxi-vm:~$ sudo docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
b901d36b6f2f: Pull complete 
0a6ba66e537a: Pulling fs layer 
Pulling repository docker.io/library/hello-world
975b84d108f1: Download complete 
3f12c794407e: Download complete 
Status: Downloaded newer image for hello-world:latest
docker.io/library/hello-world: this image was pulled from a legacy registry.  Important: This registry version will not be supported in future versions of docker.

Hello from Docker.
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker Hub account:
 https://hub.docker.com

For more examples and ideas, visit:
 https://docs.docker.com/userguide/

---Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  aufs-tools cgroupfs-mount git git-man liberror-perl
Suggested packages:
  git-daemon-run git-daemon-sysvinit git-doc git-el git-email git-gui gitk
  gitweb git-arch git-cvs git-mediawiki git-svnSetting up docker-engine (1.9.0-0~wily) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for systemd (225-1ubuntu9) ...
...
Setting up docker-engine (1.9.0-0~wily) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for systemd (225-1ubuntu9) ...

---
faxi@faxi-vm:~$ sudo sudo apt-get install linux-image-extra-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-image-extra-4.2.0-17-generic is already the newest version.
linux-image-extra-4.2.0-17-generic set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.

---
faxi@faxi-vm:~$ sudo apt-cache policy docker-engine
docker-engine:
  Installed: (none)
  Candidate: 1.9.0-0~wily
  Version table:
     1.9.0-0~wily 0
        500 https://apt.dockerproject.org/repo/ ubuntu-wily/main amd64 Packages
     1.9.0-0~vivid 0
        500 https://apt.dockerproject.org/repo/ ubuntu-vivid/main amd64 Packages
     1.9.0-0~trusty 0
        500 https://apt.dockerproject.org/repo/ ubuntu-trusty/main amd64 Packages
     1.9.0-0~precise 0
        500 https://apt.dockerproject.org/repo/ ubuntu-precise/main amd64 Packages
---


faxi@faxi-vm:~$ sudo apt-get purge lxc-docker*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'lxc-docker' for regex 'lxc-docker*'
Note, selecting 'lxc-docker-virtual-package' for regex 'lxc-docker*'
Package 'lxc-docker' is not installed, so not removed
Package 'lxc-docker-virtual-package' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.
---
faxi@faxi-vm:~$ sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
[sudo] password for faxi: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --homedir /tmp/tmp.DdDHScngQe --no-auto-check-trustdb --trust-model always --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
gpg: requesting key 2C52609D from hkp server p80.pool.sks-keyservers.net
gpg: key 2C52609D: public key "Docker Release Tool (releasedocker) <docker@docker.com>" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
---
faxi@faxi-vm:~$ uname -r
4.2.0-17-generic

