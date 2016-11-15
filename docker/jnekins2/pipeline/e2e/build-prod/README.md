# Production Image 建置


## Production Dockerfile

```
FROM agileworks/sails_sample_env
COPY ./ /sailsSample
WORKDIR /sailsSample

EXPOSE 5011
CMD 'npm start --production'
```

繼承 Dojo 1 docker image 之 dockerfile。

與 Dojo 1 進行測試時透過 `-v` 進行程式碼掛載不同，若是 Production Image 需要將相關檔案直接複製到 Image 內，如此一來就可以直接透過 `docker pull` 進行使用。

且直接定義 `CMD` 以便透過 `docker run` 直接使用。

## Production Image 建置步驟

```
stage('production'){
  sh "docker build -t agileworks/sails_sample_prod ."
  try{
    sh "docker rm -f sails_sample_prod"
  } catch(e) {}
  sh "docker run -d --name sails_sample_prod -p 8800:5011 --restart always agileworks/sails_sample_prod"
}
```

這邊略過發布程序，直接使用建置好的 `agileworks/sails_sample_prod` 進行運作，並且加上 `--restart always` 即使 Server 重開機該運作中的 Container 也會自動重啟。
