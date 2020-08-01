# Zookeeper Docker

## Usage

```shell script
git clone https://github.com/zcy0521/zookeeper-docker.git
cd zookeeper-docker
docker-compose up -d
docker-compose ps
```

## Docker

### Install

- [Debian](https://docs.docker.com/install/linux/docker-ce/debian)

```shell script
sudo apt-get update
sudo apt-get install apt-transport-https ca-certificates curl gnupg2 software-properties-common
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
sudo apt-key fingerprint 0EBFCD88
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian $(lsb_release -cs) stable"
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
sudo docker run hello-world
```
  
### Docker Compose

- [Linux](https://docs.docker.com/compose/install/#install-compose-on-linux-systems)

```shell script
sudo curl -L "https://github.com/docker/compose/releases/download/1.25.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

### Docker run Zookeeper

[Docker Hub](https://hub.docker.com/_/zookeeper)

```shell script
sudo docker pull zookeeper
sudo docker run -d --name zookeeper -p 2181:2181 -v /var/lib/zookeeper:/data zookeeper
sudo docker exec -it zookeeper bash
sudo docker stop zookeeper
sudo docker rm zookeeper
```

## Zookeeper

### Clustered (Multi-Server) Setup

[Clustered (Multi-Server) Setup](https://zookeeper.apache.org/doc/current/zookeeperAdmin.html#sc_zkMulitServerSetup)

```
tickTime=2000
dataDir=/var/lib/zookeeper/
clientPort=2181
initLimit=5
syncLimit=2
server.1=zoo1:2888:3888
server.2=zoo2:2888:3888
server.3=zoo3:2888:3888
```
