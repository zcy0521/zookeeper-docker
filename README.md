# Zookeeper

## Usage

```shell script
# 安装docker-compose
sudo curl -L "https://github.com/docker/compose/releases/download/1.24.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose

git clone https://github.com/zcy0521/zookeeper-docker.git
cd zookeeper-docker

# 运行 zookeeper
sudo docker-compose -f stack.yml up -d
```

## Docker

[Docker Hub](https://hub.docker.com/_/zookeeper)

[ZooKeeper Documentation](https://zookeeper.apache.org/doc/current/zookeeperAdmin.html)

```shell script
sudo docker pull zookeeper
sudo docker run -d --name zookeeper -p 2181:2181 -v /var/lib/zookeeper:/data zookeeper
sudo docker exec -it zookeeper bash
sudo docker stop zookeeper
sudo docker rm zookeeper
```
