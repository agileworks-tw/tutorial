ubuntu docker install
=====================

```
sudo apt-key adv --keyserver hkp://pgp.mit.edu:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
sudo add-apt-repository "deb https://apt.dockerproject.org/repo ubuntu-$(lsb_release -s -c) main"
sudo apt-get update
sudo apt-get install docker-engine
```

設定 user 可以執行 docker
-------------------------

```
sudo groupadd docker
sudo usermod -a -G docker {username}
sudo service docker restart
```

確認安裝是否完成
----------------

```
docker -v
docker ps
docker run hello-world
```

### 注意事項

如果還是不行，可以重開 ubuntu 再次[確認安裝是否完成]。

docker-compose install
----------------------

下述指令請用 `root` 執行

```
curl -L https://github.com/docker/compose/releases/download/1.6.2/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
```

docker-machine install
----------------------

下述指令請用 `root` 執行

```
curl -L https://github.com/docker/machine/releases/download/v0.5.0/docker-machine_linux-amd64.zip >machine.zip && \
unzip machine.zip && \
rm machine.zip && \
mv docker-machine* /usr/local/bin
```
