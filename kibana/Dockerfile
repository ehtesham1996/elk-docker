#Making ubuntu OS as base
FROM ubuntu:18.04

#Updating the default system
RUN apt-get update

#Installing some essentials
RUN apt-get install curl nano wget gnupg apt-transport-https -y

#Adding repository of kibana
RUN wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | apt-key add -
RUN echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | tee -a /etc/apt/sources.list.d/elastic-7.x.list

#updating system
RUN apt-get update

#installing kibana
RUN apt-get install kibana -y

#Copying configuration files
COPY kibana.yml /etc/kibana/kibana.yml

#exposing ports 
EXPOSE 5601

#Enabling to always execute kibana at startup
ENTRYPOINT service kibana restart && bash