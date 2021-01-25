# Forked from https://github.com/William-Yeh/docker-ansible/blob/master/ubuntu18.04/Dockerfile
# Dockerfile for building Ansible image for Ubuntu 18.04 (Bionic), with as few additional software as possible.
#
# @see https://launchpad.net/~ansible/+archive/ubuntu/ansible
#
# Version  1.0
#


# pull base image
FROM ubuntu:20.04

MAINTAINER William Yeh <william.pjyeh@gmail.com>


RUN echo "===> Installing Ansible..."  && \
    apt-get update && \
    apt-get install -y ansible  && \
    \
    \
    echo "===> Installing handy tools (not absolutely required)..."  && \
    apt-get install -y python3-pip                  && \
    pip3 install --upgrade pycrypto pywinrm          && \
    apt-get install -y sshpass openssh-client rsync && \
    \
    \
    echo "===> Adding hosts for convenience..."  && \
    echo 'localhost' > /etc/ansible/hosts


# default command: display Ansible version
CMD [ "ansible-playbook", "--version" ]
