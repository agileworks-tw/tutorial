# 使用 Dockerfile 建立 Docker image

使用 Dockerfile 時，一旦開始進行建置，Docker 會把 Dockerfile 所在位置底下所有的檔案載入以便建置過程中使用，為了加速建置程序，一般來說一個 Dockerfile 請放置於獨立的資料夾

## 建立 Dockerfile 存放之資料夾

```
mkdir jenkins_dockerfile
cd jenkins_dockerfile
```

## 建立 Dockerfile

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

## 進行 Dockerfile build

```
docker build -t agileworks/jenkins_auto .
```

## 運行透過 Dockerfile 建置好的 jenkins image

```
docker run -d \
--name jenkins_auto \
-p 80:8080 \
agileworks/jenkins_auto
```

如此我們可以透過下面網址存取透過 Dockerfile 建置完成的 Jenkins

`http://localhost`
