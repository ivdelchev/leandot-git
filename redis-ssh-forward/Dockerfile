FROM debian:stable

## Create a user docker, which is in the staff group
RUN useradd docker \
	&& mkdir /home/docker \
	&& chown docker:docker /home/docker \
	&& addgroup docker staff

## Install openssh, bindfs and kmod
RUN apt-get update \
  && apt-get install -y --no-install-recommends openssh-client bindfs kmod\
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/

## Install bindfs to be able to mount SSH keys from the host with the right permissions
## NOTE: you stil need to "mount -a" as root when starting the container (no autostart)
RUN mkdir /home/docker/.ssh \
  && mkdir /home/docker/.ssh-external \
  && echo "bindfs#/home/docker/.ssh-external /home/docker/.ssh fuse force-user=docker,force-group=docker,perms=0700 0 0" >> /etc/fstab
RUN chown -R docker:docker /home/docker/.ssh-external