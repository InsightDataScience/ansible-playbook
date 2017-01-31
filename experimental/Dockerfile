FROM ubuntu

RUN apt-get update \
	&& apt-get install -y software-properties-common \
	&& apt-add-repository ppa:ansible/ansible \
	&& apt-get update \
	&& apt-get install -y ansible \
	&& apt-get install -y python-pip \
	&& apt-get install vim

RUN pip install boto

