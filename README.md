# Zookeeper

[Docker Hub](https://hub.docker.com/_/zookeeper)

## docker-compose

- install

[Install Docker Compose](https://docs.docker.com/compose/install/)

```shell script
$ sudo curl -L "https://github.com/docker/compose/releases/download/1.24.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
$ sudo chmod +x /usr/local/bin/docker-compose
```

- stack.yml

```yaml
version: '3.1'

services:
  zookeeper1:
    image: zookeeper
    restart: always
    hostname: zookeeper1
    container_name: zookeeper1
    ports:
      - 2181:2181
    volumes:
      - ${HOME}/appdata/zookeeper/zookeeper1/data:/data
      - ${HOME}/appdata/zookeeper/zookeeper1/datalog:/datalog
      - ${HOME}/appdata/zookeeper/zookeeper1/logs:/logs
    environment:
      ZOO_MY_ID: 1
      ZOO_SERVERS: server.1=0.0.0.0:2888:3888;2181 server.2=zookeeper2:2888:3888;2181 server.3=zookeeper3:2888:3888;2181
      ZOO_LOG4J_PROP: INFO,ROLLINGFILE

  zookeeper2:
    image: zookeeper
    restart: always
    hostname: zookeeper2
    container_name: zookeeper2
    ports:
      - 2182:2181
    volumes:
      - ${HOME}/appdata/zookeeper/zookeeper2/data:/data
      - ${HOME}/appdata/zookeeper/zookeeper2/datalog:/datalog
      - ${HOME}/appdata/zookeeper/zookeeper2/logs:/logs
    environment:
      ZOO_MY_ID: 2
      ZOO_SERVERS: server.1=zookeeper1:2888:3888;2181 server.2=0.0.0.0:2888:3888;2181 server.3=zookeeper3:2888:3888;2181
      ZOO_LOG4J_PROP: INFO,ROLLINGFILE

  zookeeper3:
    image: zookeeper
    restart: always
    hostname: zookeeper3
    container_name: zookeeper3
    ports:
      - 2183:2181
    volumes:
      - ${HOME}/appdata/zookeeper/zookeeper3/data:/data
      - ${HOME}/appdata/zookeeper/zookeeper3/datalog:/datalog
      - ${HOME}/appdata/zookeeper/zookeeper3/logs:/logs
    environment:
      ZOO_MY_ID: 3
      ZOO_SERVERS: server.1=zookeeper1:2888:3888;2181 server.2=zookeeper2:2888:3888;2181 server.3=0.0.0.0:2888:3888;2181
      ZOO_LOG4J_PROP: INFO,ROLLINGFILE
```

- 运行

```shell script
$ sudo docker-compose -f stack.yml up -d
```
