# 建置與測試專案

## 建置專案

延續 Dojo 1 的練習進行 docker image `agileworks/sails_sample_env` 的建置，並且透過該 image 進行專案建置。

```
stage('build'){
  sh "docker build -t agileworks/sails_sample_env dockers/node"
  sh "docker-compose run --rm build"
}
```



## 專案測試

延續 Dojo 1 的練習，進行前端 e2e 測試，並且加上 UAT 預覽測試，若確認沒有問題在進行 production image 的建置。

```
stage('test'){
  sh "docker-compose run --rm --service-ports --name debug test"

  sh "docker-compose run -d --rm --service-ports --name dev dev"
  try{
    def url = 'http://localhost:5001/'
    input message: "Does staging at $url look good? ", ok: "ok! build production image."
  }finally{
    sh "docker rm -f dev"
  }
}
```

上述相關 docker-compose service 參考 [完整 docker-compose](../docker-compose/README.md) 章節
