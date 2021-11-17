FROM python:slim-buster

### -------------------------------------------------
### Metadata information
### -------------------------------------------------
LABEL name="vxlan-erb-dallas"
LABEL maintainer="cremsburg@protonmail.com"
LABEL description="ansible container to manage juniper data centers"
LABEL license="GPLv3"
LABEL url="https://gitlab.com/cremsburg/juniper-automation-container/container_registry"
LABEL build-date="20210313"

### -------------------------------------------------
### Change directory to /home/tmp
### -------------------------------------------------
WORKDIR /home/tmp/files

### -------------------------------------------------
### Add and install python packages
### -------------------------------------------------
ADD config/requirements.txt requirements.txt
RUN pip install -r requirements.txt
RUN pip install --upgrade pip

### -------------------------------------------------
### Install Ansible Galaxy roles
### -------------------------------------------------
RUN ansible-galaxy install juniper.junos -p ~/.ansible/roles

### -------------------------------------------------
### Copy local files to container
### -------------------------------------------------
COPY config/ansible.cfg /etc/ansible/ansible.cfg
COPY config/jsnapy.cfg /etc/jsnapy/jsnapy.cfg

### -------------------------------------------------
### Environmentals
### -------------------------------------------------
ENV ANSIBLE_CONFIG /etc/ansible/ansible.cfg
