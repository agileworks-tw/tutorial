# 透過 image 運行為 Container 後進行 Jenkins image 建立

## 取得基本的 ubuntu:latest image

`docker pull ubuntu:latest`

## 運行 Container 並且使用 TTY

`docker run -it --name ubuntu_base ubuntu:lastest`

上述指令將進入 Container 可進行後續指令操作，執行後將會有下列輸出

```
root@867c2a60f6b3:/#
```

表示透過 root user 操作 867c2a60f6b3 之 Container，其中

`--name ubuntu_base`

將可以在後續的操作利用別名的方式來進行。

## 進行 jenkins 的安裝

延續上一步驟已進入 ubuntu Container，執行下列指令

```
sudo apt-get install -y wget
wget -q -O - https://jenkins-ci.org/debian/jenkins-ci.org.key | sudo apt-key add -
sudo sh -c 'echo deb http://pkg.jenkins-ci.org/debian binary/ > /etc/apt/sources.list.d/jenkins.list'
sudo apt-get update
sudo apt-get install -y jenkins
```

安裝完成後，在透過下列指令確認安裝已完成

```
jenkins -v
java --version
```

## 將安裝完相關套件目前 Container 進行 commit

在 Container 內執行 exit 如下

`root@867c2a60f6b3:/# exit`

隨即運行中的 Container 將會立即 stop，我們透夠剛剛賦予的別名 `ubuntu_base` 來進行後續的操作，透過下面指令將 Container commit 為新的 image

`docker commit ubuntu_base jenkins_ubuntu`

如此，將會有一新的 image 名為 `jenkins_ubuntu` 可作為使用

## 運行製作完成的 image

透過下面指令就可以運行製作完成之 Jenkins Docker image

```
docker run -d \
-p 8000:8080 \
--name jenkins \
jenkins_ubuntu \
su jenkins -c "java -jar /usr/share/jenkins/jenkins.war"
```

一旦運行完成，將可以透過下列指令進入 jenkins 管理介面

`http://localhost:8000/`
