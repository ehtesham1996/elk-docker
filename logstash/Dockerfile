#Using ubuntu as base image
FROM ubuntu:18.04

#Updating the current system
RUN apt-get update

#Installing some essentials
RUN apt-get install nano wget apt-transport-https gnupg -y

#installing java
RUN apt-get install -y default-jdk openjdk-8-jre

#Setting JAVA_HOME environment variable because later on to be used by logstash installation
ENV JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64/jre

#Adding repository of logstash
RUN wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | apt-key add -
RUN echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | tee -a /etc/apt/sources.list.d/elastic-7.x.list

#updating system
RUN apt-get update

#installing logstash
RUN apt-get install logstash -y

#copying config files
COPY logstash.yml /etc/logstash/logstash.yml
COPY syslog.conf /etc/logstash/conf.d/syslog.conf

#expose port 5000 to listen syslog feed
EXPOSE 5000

#Enabling to always execute logstash at startup
ENTRYPOINT service logstash restart && bash
