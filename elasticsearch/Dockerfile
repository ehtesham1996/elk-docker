#Using ubuntu as operatin system
FROM ubuntu:18.04

#Updating the default system
RUN apt-get update

#Installing some Essential packages with description given in comments

#Installing curl just ot test localhost request inside container
RUN apt-get install curl -y

#Installing nano for some editing inside container
RUN apt-get install nano -y

#Installing https wget gnupg for downloading packages
RUN apt-get install -y apt-transport-https wget gnupg

#Installing software-properties-common to make sure add-apt-repo.. will work later on
RUN apt-get install -y software-properties-common

#Now installing java8 as it;s prereq of elasticsearch
RUN apt-get install -y default-jdk openjdk-8-jre

#Setting JAVA_HOME environment variable because later on to be used by elasticserach installation
ENV JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64/jre

#Now installing elastic search ref : https://tecadmin.net/setup-elasticsearch-on-ubuntu/
RUN wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | apt-key add - 

RUN add-apt-repository "deb https://artifacts.elastic.co/packages/7.x/apt stable main"
#Updating after adding repository/
RUN apt-get update
#Installing elastic now
RUN apt-get install elasticsearch -y

#Adding elastic serach configurations
COPY elasticsearch.yml /etc/elasticsearch/elasticsearch.yml

#Exposing the elastic port
EXPOSE 9200

#Enabling to always execute elasticsearch at startup
ENTRYPOINT service elasticsearch restart && bash