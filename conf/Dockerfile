########################################################
# Dockerfile for ansible-playbook
# Based on debian
########################################################

FROM ubuntu

MAINTAINER Ronak Nathani

RUN apt-get update \
	&& apt-get install -y software-properties-common \
	&& apt-add-repository ppa:ansible/ansible \
	&& apt-get update \
	&& apt-get install -y ansible \
	&& apt-get install -y python-pip \
	&& apt-get install -y vim \
    && apt-get install -y git

RUN pip install boto

COPY . /root/ansible-playbook

RUN rm /etc/ansible/hosts
RUN mkdir /etc/ansible/hosts/

COPY ansible_example.cfg /etc/ansible/ansible.cfg
COPY ec2.py /etc/ansible/hosts/
COPY ec2.ini /etc/ansible/hosts/
