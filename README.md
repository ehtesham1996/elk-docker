# elk-docker
Deploying ELK stack on docker using three different containers and interlinking them

---
## Description
This repository is composed of ELK stack .ELasticseacrh , Kibana and Logstash. All logs from syslog are configure to forward through logstash to elastic container and kibana desktop is used to visually display these log details.

---
## Requirements
### Host setup
- Docker Engine version 17.05+
- Docker Compose version 1.12.0+

---
## Usage:

#### **Clone the repository**:
  - `git clone https://github.com/ehtesham1996/elk-docker.git` 

#### **Kill already running 5000 9200 5601 port**:
  - `kill $(lsof -t -i:5000)`
  - `kill $(lsof -t -i:9200)`
  - `kill $(lsof -t -i:5601)`

#### **Compile the docker file**:
  - `docker-compose up`
