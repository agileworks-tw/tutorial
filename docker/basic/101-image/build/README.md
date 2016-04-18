# docker image 建立

docker image 的建立，將介紹兩種方式

1. 透過 image 運行為 Container 後透過 bash 進行 image 建立
2. 透過 Dockerfile 定義進行 image 建立

兩個範例都將透過安裝 Jenkins Server 來進行。

## 透過 image 運行為 Container 後進行 image 建立

### 取得基本的 ubuntu:latest image

`docker pull ubuntu:latest`

### 運行 Container 並且使用 TTY

`docker run -it --name ubuntu_base ubuntu:lastest`

上述指令將進入 Container 可進行後續指令操作，執行後將會有下列輸出

```
root@867c2a60f6b3:/#
```

表示透過 root user 操作 867c2a60f6b3 之 Container，其中

`--name ubuntu_base`

將可以在後續的操作利用別名的方式來進行。

### 進行 jenkins 的安裝

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

### 將安裝完相關套件目前 Container 進行 commit

在 Container 內執行 exit 如下

`root@867c2a60f6b3:/# exit`

隨即運行中的 Container 將會立即 stop，我們透夠剛剛賦予的別名 `ubuntu_base` 來進行後續的操作，透過下面指令將 Container commit 為新的 image

`docker commit ubuntu_base jenkins_ubuntu`

如此，將會有一新的 image 名為 `jenkins_ubuntu` 可作為使用

### 運行製作完成的 image

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

## 使用 Dockerfile 建立 Docker image

使用 Dockerfile 時，一旦開始進行建置，Docker 會把 Dockerfile 所在位置底下所有的檔案載入以便建置過程中使用，為了加速建置程序，一般來說一個 Dockerfile 請放置於獨立的資料夾

### 建立 Dockerfile 存放之資料夾

```
mkdir jenkins_dockerfile
cd jenkins_dockerfile
```

### 建立 Dockerfile

```
cat > Dockerfile <<EOL
FROM ubuntu:14.04

RUN sudo apt-get install -y wget
RUN wget -q -O - https://jenkins-ci.org/debian/jenkins-ci.org.key | sudo apt-key add -
RUN sudo sh -c 'echo deb http://pkg.jenkins-ci.org/debian binary/ > /etc/apt/sources.list.d/jenkins.list'
RUN sudo apt-get update
RUN sudo apt-get install -y jenkins

EXPOSE 8080
CMD su jenkins -c 'java -jar /usr/share/jenkins/jenkins.war'
EOL
```

與 `透過 image 運行為 Container 後進行 image 建立` 安裝步驟類似，透過 Dockerfile 將可以更加簡化，其中本來在執行 `run` 時所需指令直接定義在 Dockerfile 內。

### 進行 Dockerfile build

```
docker build -t agileworks/jenkins_auto .
```

### 運行透過 Dockerfile 建置好的 jenkins image

```
docker run -d \
--name jenkins_auto \
-p 80:8080 \
agileworks/jenkins_auto
```

如此我們可以透過下面網址存取透過 Dockerfile 建置完成的 Jenkins

`http://localhost`
