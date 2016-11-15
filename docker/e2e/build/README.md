# 建置專案 Docker 環境

## dockerfile

```
FROM mhart/alpine-node:5.12.0

RUN apk add --update git
RUN apk add --update build-base libffi-dev ruby ruby-dev \
    && gem install sass compass --no-ri --no-rdoc \
    && apk del build-base libffi-dev ruby-dev \
    && rm -rf /var/cache/apk/*

RUN apk add --no-cache make gcc g++ python && rm -rf /var/cache/apk/*
```

此專案使用到主要的語言為

* nodejs 5.12.0
* ruby

## 建置 docker image

`docker build -t agileworks/sails_sample_env dockers/node`

透過 `docker images` 指令將會看到下面結果

```
REPOSITORY                          TAG                 IMAGE ID            CREATED             SIZE
agileworks/sails_sample_env         latest              9cb830d5db2e        10 hours ago        266.2 MB
```
