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

## docker production 發布流程練習

```
docker login -e test@gmail.com -p testpass -u testuser
docker-compose run package
docker build -t smlsunxie/sample_prod .
docker push smlsunxie/sample_prod
```
