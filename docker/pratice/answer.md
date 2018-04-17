# 相關練習解答

## 製作 docker-compose 之 dev mode service

```
data:
  image: ubuntu
  volumes:
    - /root/.m2

server:
  image: maven:3-jdk-8
  volumes:
    - ./:/app
  volumes_from:
    - data
  working_dir: /app
  ports:
   - "8000:8000"
  command: "/bin/bash"
```

## 啟動 private registry

`docker run -d -p 5000:5000 --restart=always --name registry registry:2`

## docker production 發布流程練習

```
docker-compose run package
docker build -t localhost:5000/sample_prod .
docker push localhost:5000/sample_prod
```

## 使用 production image 運行專案進行 preview

```
docker stop preview
docker rm preview
docker run -d -p 8000:8000 --name preview localhost:5000/sample_prod
```

## jenkins 建立 production deploy task

### task shell script

```
docker login -e test@gmail.com -p testpass -u testuser
docker-compose run package
docker build -t localhost:5000/sample_prod .
docker push localhost:5000/sample_prod
```

### 透過 ssh 連線到 production 機器運行建置好的 image

```
ssh jenkins@localhost ' \

  docker stop prod && \
  docker rm prod && \
  docker run -d -p 8800:8800 --restart always --name prod localhost:5000/sample_prod \

'
```
