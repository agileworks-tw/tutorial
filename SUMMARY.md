# Summary

- 上課須知
  - [相關服務事前註冊](prepare/service-signup.md)
  - [事前安裝：自備筆電](prepare/laptop.md)
  - [事前安裝：電腦教室](prepare/pc.md)




<!--   

  - [初始 Git 專案](git/start/README.md)
  - [clone 已建立之遠端專案](git/clone/README.md)
  - [log 使用](git/log/README.md)
  - status 使用
  - [建立 Branch (分支)](git/branch/README.md)

  - workspace 到 remote repository  
    - git rm / git mv
    - git add
    - git commit
    - git commit -a
    - [git push](git/push/README.md)

  - remote repository 到 workspace
    - [git fetch remote 專案最新變動(不合併遠端分支)](git/fetch/README.md)
    - git reset --soft
    - git checkout 

    - git pull / git reset --hard remote/branch
    - [git Pull remote 專案最新變動(合併遠端分支)](git/pull/README.md)

    - git merge
    - [git merge Branch (分支)](git/merge/README.md)

    - git checkout HEAD / git reset --hard
    - [git checkout HEAD](git/checkout/README.md)
  
  - workspace 到 stash
    - git stash
    - git stash apply

  - [編修衝突](git/conflict/README.md)  
  - [tag 使用](git/tag/README.md)

  - 其他 GitHub 功能
    - pull request
    - issues

  - [什麼是 Git Flow](git/flow/README.md)
  - 
  - -->

  <!-- - 搭配 SourceTree 進行版本控制
    - 查看圖形化 log
    - 查看 diff
    - 編修衝突
    - Reset
    - Branch
    - merge -->
  

<!-- - JavaScript

  - [this](javascript/this/README.md)
  - [scope](javascript/scope/README.md)
  - [callback](javascript/callback/README.md)
  - [Closure](javascript/closure/README.md)
  - [settimeout](javascript/settimeout/README.md)
  - [performance](javascript/performance/README.md)
  - [Memory Leaks](javascript/memory_leak/README.md)
- TDD(測試驅動開發方式)
  - Java
    - [JUnit 基礎](./tdd/java/junit4/basic/README.md)
    - [JUnit 與 Maven](./tdd/java/junit4/maven/README.md)
    - [Assertions](./tdd/java/junit4/assertions/README.md)
    - [Test Fixtures](./tdd/java/junit4/test-fixture/README.md)
    - [略過 test](./tdd/java/junit4/test-fixture/README.md)
    - [Junit 測試 API](./tdd/java/junit4/api-test/README.md)
    - [JUnit Test Suite](./tdd/java/junit4/suite/README.md) -->

- Jenkins

  * [Introduction](jenkins/README.md)
  * [基本概念介紹](jenkins/basic/README.md)
     * [豐田式生產](jenkins/basic/lean.md)
     * [敏捷式開發](jenkins/basic/agile.md)
     * [持續整合](jenkins/basic/continuous-integration.md)
     * [安裝 Jenkins](jenkins/basic/install.md)
       
  * [Quick Start](jenkins/workshop/README.md)
     * [Lab 101](jenkins/workshop/lab101.md)
     * [Lab 102](jenkins/workshop/lab102.md)
     * [Lab 103](jenkins/workshop/lab103.md)
     * [Lab 104](jenkins/workshop/lab104.md)
     
  * [CI flow 簡介](jenkins/task/flow.md)
  * [持續整合實作以 Java + git 為例](jenkins/task/java_git/README.md)
    * [Lab 進行方式說明](jenkins/task/README.md)
    * Lab 201 建置 
      * [build-package](jenkins/task/java_git/build.md)
      * [build-archive](jenkins/common/build-archive.md)
    * Lab 202 測試
      * [test](jenkins/task/java_git/test.md)
      * [plugin-JUnit](jenkins/common/test-report.md)
      * [plugin-Cobertura](jenkins/plugin/cobertura.md)
    * Lab 203 部署
      * [ssh-遠端連線設置](jenkins/setup/ssh.md)
      * [使用 ssh 進行 deploy](jenkins/task/java_git/release.md)
    * Lab 204 Task 連結 與 Build Trigger
      * [定期建置 Trigger](jenkins/task/cron_test.md)
      * [Pull SCM Trigger](jenkins/task/pull_scm/README.md)
      * [Task 連結-測試成功則進行部署](jenkins/task/if_test_ok_then_preview.md)
  
  * [搭配 Jenkins 2.0 之 Pipeline 進行建置](jenkins/jenkins2/README.md)
     * [基礎練習](jenkins/jenkins2/pipeline/tutorial/README.md)
     * [使用 Pipeline 進行建置](jenkins/jenkins2/pipeline/build/README.md)
     * [使用 GitHub Organization 進行建置](jenkins/jenkins2/github-organization/README.md)
     * [使用 Multibranch Pipeline 進行建置](jenkins/jenkins2/multibranch-pipeline/README.md)

  * 設定
     * [環境變數](jenkins/setup/env.md)
     * [ssh 與 scp](jenkins/setup/ssh.md)

  * 進階設定
     * [security](jenkins/setup/security.md)
     * [timezone](jenkins/setup/timezone.md)
     * [master/slave](jenkins/setup/master-slave.md)

  <!-- * Jenkins CI 常用功能
     
     * [Plugin 安裝](jenkins/common/plugin.md)
     * [執行 Shell Script](jenkins/common/shell.md)
     * [Jenkins API 使用簡介](jenkins/common/api.md)
     * [Subversion 整合](jenkins/common/subversion.md)   
     * [Script Console](jenkins/common/script-console.md) -->
  
  * [常用 plugin 介紹](jenkins/plugin/README.md)
     * [Config File Provider](jenkins/plugin/config-file-provider.md)
     * [Bitbucket](jenkins/plugin/bitbucket.md)
     * [Jira](jenkins/plugin/jira.md)
     
  
  <!-- * [Task 實作以 Node.js 為例](jenkins/task/nodejs/README.md)
     * [build](jenkins/task/nodejs/build.md)
     * [test](jenkins/task/nodejs/test.md)
     * [preview](jenkins/task/nodejs/preview.md)
     * [release](jenkins/task/nodejs/release.md) -->

  <!-- * [Task 實作以 Java + SVN 為例](jenkins/task/java_svn/README.md)
     * [專案組成](jenkins/task/java_svn/project.md)
     * [初始資料](jenkins/task/java_svn/inital.md)
     * [build](jenkins/task/java_svn/build.md)
     * [test](jenkins/task/java_svn/test.md)
     * [preview](jenkins/task/java_svn/preview.md)
     * [release](jenkins/task/java_svn/release.md) -->



  <!-- * [搭配 docker 使用 Jenkins 協助測試](jenkins/withDocker/README.md)
     * [install](jenkins/withDocker/install.md)
     * [build](jenkins/withDocker/build.md)
     * [test](jenkins/withDocker/test.md)
     * [preview](jenkins/withDocker/preview.md)
     * [release](jenkins/withDocker/release.md) -->


  <!-- * 自動化檢查與報表設置
    * [java doc 使用與報表產出設置](./jenkins/check/javadoc/README.md)
    * [Checkstyle 使用與報表產出設置](./jenkins/check/checkstyle/README.md)
    * [PMD(source code analyzer) 使用與報表產出設置](./jenkins/check/pmd/README.md)
    * [CPD(Copy/Paste Detector) 使用與報表產出設置](./jenkins/check/dry/cpd//README.md)
    * [Simian 使用與報表產出設置](./jenkins/check/dry/simian/README.md)
    * [FindBugs 使用與報表產出設置](./jenkins/check/findBugs/README.md) -->
  <!-- * 建置工具
    * maven
      * [Multi Module Project](./jenkins/maven/multi-app/README.md) -->

  * Q & A
     * [一般問題](jenkins/QA/general.md)
     * [JAVA](jenkins/QA/java.md)

- [Docker](docker/README.md)
  - [Meet Docker](docker/000-intro/README.md)
    - [What is Docker](docker/000-intro/what/README.md)
    - [Docker vs VMs](docker/000-intro/compare/README.md)
    - [Why Docker](docker/000-intro/why/README.md)
    - [Image](docker/000-intro/image/README.md)
    - [Container](docker/000-intro/container/README.md)
    - [Repository](docker/000-intro/repository/README.md)
    - [Registry](docker/000-intro/registry/README.md)

  - [command reference](docker/basic/command_ref/README.md)

  - [Lab 101: Docker Image](docker/basic/101-image/README.md)

    - [help](docker/basic/101-image/help/README.md)
    - [search](docker/basic/101-image/search/README.md)
    - [pull](docker/basic/101-image/pull/README.md)
    - [images](docker/basic/101-image/images/README.md)
    - [inspect](docker/basic/101-image/inspect/README.md)
    - [save, load](docker/basic/101-image/save-load/README.md)
    - [rmi](docker/basic/101-image/rmi/README.md)

  - [Lab 102: Docker Container](docker/basic/102-container/README.md)

    - [create, start, stop, ps](docker/basic/102-container/create/README.md)
    - [run](docker/basic/102-container/run/README.md)
    - [run -d](docker/basic/102-container/daemon/README.md)
    - [exec, attach](docker/basic/102-container/exec/README.md)
    - [rm](docker/basic/102-container/rm/README.md)

  - [Lab 103: Registry](docker/basic/103-registry/README.md)

    - [distribution private](docker/basic/103-registry/distribution-private/README.md)
    - [distribution public](docker/basic/103-registry/distribution-public/README.md)

  - Lab 104: dockerfile

    - [CMD vs entrypoint](docker/basic/104-dockerfile/entrypoint/README.md)

  - [Lab 201: Docker volume](docker/basic/201-volume/README.md)

    - [create, inspect](docker/basic/201-volume/create/README.md)
    - [direct volume host filesystem](docker/basic/201-volume/direct/README.md)
    - [volume form container](docker/basic/201-volume/volume_from/README.md)

  - [Lab 202: Docker network](docker/basic/202-network/README.md)

    - [link](docker/basic/202-network/link/README.md)
    - [expose](docker/basic/202-network/expose/README.md)
    - [create](docker/basic/202-network/create/README.md)
    - [port](docker/basic/202-network/port/README.md)
    - [透過 docker-compose 使用 network](docker/basic/202-network/docker-compose/README.md)

  - [Lab 203: Docker Machine 的使用 (1 hour)](docker/machine/README.md)
    - [install](docker/machine/install/README.md)
    - [drive](docker/machine/drive/README.md)
    - [create](docker/machine/create/README.md)
    - [env](docker/machine/env/README.md)
    - [ls](docker/machine/ls/README.md)
    - [使用 docker-machine 連結已存在之遠端 docker engine](docker/machine/exist-remote-docker/README.md)
    - [upgrade](docker/machine/upgrade/README.md)
    - [rm](docker/machine/rm/README.md)
  - Lab 301: 使用 docker 建置 java 開發環境 (1 hour)
    - [運行環境安裝](docker/project/java/env/README.md)
    - [進入 Container 進行建置](docker/project/java/env-docker-build/README.md)
    - [透過 Dockerfile 進行建置](docker/project/java/env-dockerfile/README.md)

  - Lab 302: 使用 docker 建置 Jenkins 服務 (1 hour)

    - [進入 Container 進行建置](docker/application/jenkins/build-docker/README.md)
    - [透過 Dockerfile 進行建置](docker/application/jenkins/build-dockerfile/README.md)

  - Lab 401: java 範例專案使用 docker 進行建置 (1 hour)

    - [範例專案](docker/project/java/repository/README.md)
    - [安裝](docker/project/java/mvn-install/README.md)
    - [測試](docker/project/java/mvn-test/README.md)
    - [運行](docker/project/java/mvn-run/README.md)
    - [打包](docker/project/java/mvn-package/README.md)

  - Lab 402: docker-compose
    - [run and up](docker/compose/run_up/README.md)
    - [其他指令](docker/compose/other_command/README.md)

  - Lab 403: java 範例專案使用 docker-compose 進行建置 (1 hour)

    - [練習：製作 dev mode service](docker/pratice/compose-dev-mode.md)
    - [範例專案](docker/project/java/repository/README.md)
    - [安裝](docker/project/java/compose-mvn-install/README.md)
    - [測試](docker/project/java/compose-mvn-test/README.md)
    - [運行](docker/project/java/compose-mvn-run/README.md)
    - [打包](docker/project/java/compose-mvn-package/README.md)

  - Lab 404: java 範例專案進行 production 並且搭配 jenkins (1 hour)

    - [production image 製作](docker/project/java/production-image-build/README.md)
    - [練習：docker production 發布流程](docker/pratice/production-image-publish.md)
    - [練習：使用 production image 運行專案](docker/pratice/production-image-run.md)
    - [練習：搭配 jenkins 建立 production deploy task](docker/pratice/jenkins-docker-prod-deploy-task.md)

  - [Lab 405: 使用 Docker 進行前端自動化測試 (1 hour)](docker/e2e/README.md)
    * [建置專案 Docker 環境](docker/e2e/build/README.md)
    * [透過 Docker 運行專案](docker/e2e/docker-debug/README.md)
    * [透過 Docker 運行專案並執行 e2e test](docker/e2e/docker-e2e/README.md)

  - [Lab 501: java jenkins 2.0 Pipeline 使用 Docker 進行專案建置 (1 hour)](docker/jnekins2/pipeline/build/README.md)

  - [Lab 502: jenkins 2.0 Pipeline 使用 Docker 進行前端自動化測試 (1 hour)](docker/jnekins2/pipeline/e2e/README.md)
    * [持續整合流程說明](docker/jnekins2/pipeline/e2e/CI-flow/README.md)
    * [檢查所需環境及取出專案](docker/jnekins2/pipeline/e2e/check-checkout/README.md)
    * [建置與測試專案](docker/jnekins2/pipeline/e2e/build-test/README.md)
    * [Production Image 建置](docker/jnekins2/pipeline/e2e/build-prod/README.md)
    * [完整 docker-compose](docker/jnekins2/pipeline/e2e/docker-compose/README.md)


- Appendix

  - [vt-x amd-v 異常造成 VM 無法開啟](docker/troubleshooting/vt_x_amd_v_error/README.md)
  - [Ubuntu install docker](docker/install/ubuntu/README.md)
  - [Mac OS X install docker](docker/install/osx/README.md)
  - [docker 參考資料](docker/reference/README.md)
  - [git 參考資料](git/reference/README.md)
  - [docker 相關練習解答](docker/pratice/answer.md)
