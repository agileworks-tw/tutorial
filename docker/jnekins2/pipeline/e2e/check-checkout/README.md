# 檢查所需環境及取出專案

## check environment

檢查 Docker 是否正確安裝，及相關的版號

```
stage('check environment'){
  sh "docker -v"
  sh "docker-compose -v"
  sh "docker ps"
}
```

## checkout

透過 `git` 取出範例專案。

```
stage('checkout'){
  git url: 'https://github.com/smlsunxie/cargocms.git', branch: 'dojo2'
}
```
