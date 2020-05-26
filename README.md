FROM centos
MAINTAINER ashima mehta <ashimamehta@outlook.in>
RUN yum update -y
RUN yum install wget -y
RUN yum install python36 -y
RUN yum install python3-pip
RUN pip3 install --upgrade pip
RUN pip3 install tensorflow==2.0.0
RUN pip3 install keras
WORKDIR /model
COPY mnistdata.py /model
RUN python3 mnistdata.py
CMD python3 mlops.py
