# AWS Lightsail IOT Stack setup using docker
Setup AWS Lightsail to create docker container for IOT Stack (OS:ubuntu, Grafana, InfluxDB, NodeRed &amp; mosquitto)

## Setup steps

add this code to the 
```
curl -o lightsail-compose.sh https://raw.githubusercontent.com/shafiiub/aws-lightsail-iot-stack-using-docker/main/lightsail-compose.sh
chmod +x ./lightsail-compose.sh

./lightsail-compose.sh
```

Open Ports 
```
networking >ipv4 add ports

```

## Setup influxDB
go to the command line and the the follwoing
```
$ docker ps -a
$ docker ps
$ cd /srv/docker
$ docker-compose exec influxdb /bin/bash
root@a76c12fadfad:/# influx 
Connected to http://localhost:8086 version 1.8.3
InfluxDB shell version: 1.8.3
> show users
user admin
---- -----
> create user "iot-stack" with password 'xxxxxxxxx' with all privileges
> ;
> show users
user      admin
----      -----
iot-stack true

> CREATE DATABASE airquality
> SHOW DATABASES
name: databases
name
----
_internal
airquality

```

## Some docker commands
Some Basic commands
```
- $ docker ps  list running containers. 
- $ docker ps -a list all container including stopped container
- $ docker network create --driver bridge iotstack_net creating network bridge
- $ docker exec -it influxdb /bin/bash
  root@f7f7292006d0:/# influx

```
Docker compose commands
```
$ docker-compose up -d same location where docker-compose.yml file exists
$ docker-compose exec influxdb /bin/bash to access influxDB command inteface
$ docker-compose logs --tail=5 influxdb  attached log
```
Some combinations that help a lot:
```
- kill all running containers with docker kill $(docker ps -q)
- delete all stopped containers with docker rm $(docker ps -a -q)
- delete all images with docker rmi $(docker images -q)
- update and stop a container that is in a crash-loop with docker update --restart=no && docker stop
- bash shell into container docker exec -i -t /bin/bash - if bash is not available use /bin/sh
- bash shell with root if container is running in a different user context docker exec -i -t -u root /bin/bash

```


## Important links
- (light sail todo example) [https://github.com/mikegcoleman/todo]
- (setup IOT Stack on raspberry pi)[https://github.com/SensorsIot/IOTstack]
- (influxDB setup using docker)[https://www.influxdata.com/blog/tips-for-running-the-tick-stack-using-docker/]
- (influxDB setup using docker)[https://thenewstack.io/how-to-setup-influxdb-telegraf-and-grafana-on-docker-part-1/]
- (influxDB setup using docker)[https://devconnected.com/how-to-install-influxdb-on-ubuntu-debian-in-2019/]
- (Docker commands)[https://codenotary.com/blog/extremely-useful-docker-commands/]
