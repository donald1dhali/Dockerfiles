    
FROM ubuntu:latest
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update
RUN apt-get -y install sshpass software-properties-common
RUN apt-get -y install python3-dev libkrb5-dev krb5-user wget gcc curl

# Install sql driver and other dependencies 
RUN curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
RUN curl https://packages.microsoft.com/config/ubuntu/18.04/prod.list > /etc/apt/sources.list.d/mssql-release.list
RUN apt-get update
RUN ACCEPT_EULA=Y apt-get -y install msodbcsql17
RUN ACCEPT_EULA=Y apt-get -y install mssql-tools
RUN apt-get -y install unixodbc-dev
RUN apt-get -y install g++

RUN apt-get -y install vim
RUN wget https://bootstrap.pypa.io/get-pip.py
RUN python3 get-pip.py
RUN pip3 install pywinrm kerberos requests_kerberos botocore boto3 pyodbc ansible


RUN apt-get install -y git
RUN git clone https://github.com/dell/dellemc-openmanage-ansible-modules
RUN cd dellemc-openmanage-ansible-modules/ && python3 ./install.py