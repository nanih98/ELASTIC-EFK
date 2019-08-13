# Docker ELASTIC-EFK

## Preflight-check

```diff 
$ yum install git -y or $ apt-get install git -y or $ zypper install git -y (as root), else use sudo 
$ mkdir /root/init
$ git clone https://github.com/nanih98/ELASTIC-EFK.git /root/init
```
## Run preinstall.sh to prepare the system

```diff
$ cd /root/init/ELASTIC-EFK
$ bash preinstall.sh
$ docker-compose up -d 
```
## Check if all the containers are running correctly

```diff
$ docker-compose ps
$ docker logs traefik/fluentd/elasticsearch/kibana/curator (one by one)
```
## Change the domain name if you want to use traefik

Traefik command:

**- --docker.domain=kibana.example.com**

Kibana label (traefik host rule):

**- traefik.frontend.rule=Host:kibana.example.com**

**Then apply the changes:**

```diff
$ docker restart traefik 
```
> **Note:**  If you dont want to use traefik by the moment, allow port 5601 (kibana default port) and acces them using your public/internal ip. **Example**: 35.17.104.63:5601 in your browser. (Remember to allow the port 80-443 if you youse traefik, and 5601 if you dont want to use it and you want acces directly). **Important if you are using GCP or AWS.**

## Versioning


|                |Version                        |Comments                     |
|----------------|-------------------------------|-----------------------------|
|Kibana          |      **7.2.0**                |                             |
|Logstash        |      **7.2.0**                |                             |
|Elasticsearch   |      **7.2.0**                |                             |
|Fluentd         |      **latest**               |                             |
|Curator         |      **5.7.6**                | Necessary for elastic version 7.2.0|
