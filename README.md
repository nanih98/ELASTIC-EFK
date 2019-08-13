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
$ docker logs traefik/fluentd/elasticsearch/kibana/curator
```
## Versioning


|                |Version                        |Comments                     |
|----------------|-------------------------------|-----------------------------|
|Kibana          |      **7.2.0**                |                             |
|Logstash        |      **7.2.0**                |                             |
|Elasticsearch   |      **7.2.0**                |                             |
|Redis           |        **5**                  |                             |
|Curator         |      **5.7.6**                | Necessary for elastic version 7.2.0|
