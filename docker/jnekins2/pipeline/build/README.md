# 使用 Pipeline 透過 docker 進行建置

我們可以把前面章節所完成的相關 task 濃縮為單一個 Jenkinsfile

```
node {

  stage 'checkout project'
  git url: 'https://github.com/agileworks-tw/spring-boot-sample.git'

  stage 'check docker env'

  sh "docker -v"
  sh "docker-compose -v"
  sh "docker ps"

  stage 'build docker env'
  sh "make build-docker-env"

  stage 'test project'
  sh "docker-compose run --rm test"

  stage 'server project'
  sh "docker-compose up -d server"

  try{
    stage 'Approve, go production'
    def url = 'http://localhost:8000/'
    input message: "Does staging at $url look good? ", ok: "Deploy to production"
  }finally{
    sh "docker-compose stop server"
  }

  stage 'package project'
  sh "docker-compose run --rm package"

  stage 'build docker production image'
  sh "make build-docker-prod-image"

  stage 'publish docker production image'
  sh "docker push localhost:5000/java_sample_prod"

  stage 'deploy production'
  sh "make deploy-production-local"

}

```

執行結果如下

![](stage-view.png)

## 使用 blueocean

```
pipeline {
  agent any
  stages {
    stage('checkout project') {
      steps {
        checkout scm
      }
    }
    stage('test') {
      steps {
        sh 'docker-compose run test'
      }
    }
    stage('report') {
      parallel {
        stage('report') {
          steps {
            junit 'target/surefire-reports/*.xml'
          }
        }
        stage('coverage') {
          steps {
            cobertura(coberturaReportFile: 'target/site/cobertura/coverage.xml')
          }
        }
      }
    }
    stage('package') {
      steps {
        sh 'docker-compose run package'
      }
    }
    stage('archive') {
      steps {
        archiveArtifacts 'target/spring-boot-sample-data-rest-0.1.0.jar'
      }
    }
    stage('deploy') {
      steps {
        sh '''make build-docker-prod-image
make deploy-production-ssh
'''
      }
    }
  }
  post {
    always {
      sh 'docker-compose run clean'
      echo 'I will always say Hello again!'
    }

    success {
      echo 'success!'

    }

    failure {
      echo 'failure!'

    }

  }
}
```

![](assets/2018-07-30-14-54-03.png)