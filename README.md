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



## Important links
- (light sail todo example) [https://github.com/mikegcoleman/todo]
- (setup IOT Stack on raspberry pi)[https://github.com/SensorsIot/IOTstack]
