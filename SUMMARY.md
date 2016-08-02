# Summary

- 上課須知

  - [相關服務事前註冊](prepare/service-signup.md)
  - [事前安裝：自備筆電](prepare/laptop.md)
  - [事前安裝：電腦教室](prepare/pc.md)

- [git](./git/README.md)

  - 基礎
    - [初始 Git 專案](git/start/README.md)
    - [Push 專案至 GitHub](git/push/README.md)
    - [clone 已建立之遠端專案](git/clone/README.md)
    - [復原/取出特定版控檔案](git/checkout/README.md)
    - [log 使用](git/log/README.md)
    - [Pull remote 專案最新變動(合併遠端分支)](git/pull/README.md)
    - [fetch remote 專案最新變動(不合併遠端分支)](git/fetch/README.md)
    - [什麼是 Git Flow](git/flow/README.md)
    - [建立 Branch (分支)](git/branch/README.md)
    - [合併 Branch (分支)](git/merge/README.md)
    - [編修衝突](git/conflict/README.md)
    - [reset 使用](git/reset/README.md)
    - [tag 使用](git/tag/README.md)

  - 搭配 SourceTree 進行版本控制
    - 查看圖形化 log
    - 查看 diff
    - 編修衝突
    - Reset
    - Branch
    - merge
  - 進階
    - Stash
    - rebase
    - squash
    - revert
    - amend
    - cherry pick
    - add remote
    - fork
    - upstream sync
    - pull request
  - 其他 GitHub 功能
    - issues
    - ZenHub
    - Milestone

- javascript

  - [this](javascript/this/README.md)
  - [scope](javascript/scope/README.md)
  - [callback](javascript/callback/README.md)
  - [Closure](javascript/closure/README.md)
  - [settimeout](javascript/settimeout/README.md)
  - [performance](javascript/performance/README.md)
  - [Memory Leaks](javascript/memory_leak/README.md)
- TDD(測試驅動開發方式)
  - Java
    - [JUnit 基礎](./tdd/java/junit/basic/README.md)
    - [Junit 進行 rest api 測試](./tdd/java/junit/api-test/README.md)
    - [JUnit Suite 使用](./tdd/java/junit/junit-suite-test/README.md)

- jenkins

  * [Introduction](jenkins/README.md)
  * [Quick Start](jenkins/workshop/README.md)
     * [Lab 101](jenkins/workshop/lab101.md)
     * [Lab 102](jenkins/workshop/lab102.md)
     * [Lab 103](jenkins/workshop/lab103.md)
     * [Lab 104](jenkins/workshop/lab104.md)
  * [基本概念介紹](jenkins/basic/README.md)
     * [豐田式生產](jenkins/basic/lean.md)
     * [敏捷式開發](jenkins/basic/agile.md)
     * [持續整合](jenkins/basic/continuous-integration.md)
     * [安裝 Jenkins](jenkins/basic/install.md)
  * 設定
     * [環境變數](jenkins/setup/env.md)
     * [ssh](jenkins/setup/ssh.md)
     * [security](jenkins/setup/security.md)
     * [timezone](jenkins/setup/timezone.md)
     * [master/slave](jenkins/setup/master-slave.md)
  * Jenkins CI 常用功能
     * [build archive](jenkins/common/build-archive.md)
     * [執行 Shell Script](jenkins/common/shell.md)
     * [Jenkins API 使用簡介](jenkins/common/api.md)
     * [Plugin 安裝](jenkins/common/plugin.md)
     * [Subversion 整合](jenkins/common/subversion.md)
     * [JUnit 報表](jenkins/common/test-report.md)
     * [Script Console](jenkins/common/script-console.md)
  * [常用 plugin 介紹](jenkins/plugin/README.md)
     * [publish over ssh](jenkins/plugin/publish-over-ssh.md)
     * [Config File Provider](jenkins/plugin/config-file-provider.md)
     * [GitHub pull request builder](jenkins/plugin/github_pull_request_builder.md)
     * [Bitbucket](jenkins/plugin/bitbucket.md)
     * [Cobertura](jenkins/plugin/cobertura.md)
     * [Jira](jenkins/plugin/jira.md)
     * [使用指令安裝常用套件](jenkins/plugin/install_use_command.md)
  * [CI flow 簡介](jenkins/task/flow.md)
  * [Task 實作以 Node.js 為例](jenkins/task/nodejs/README.md)
     * [build](jenkins/task/nodejs/build.md)
     * [test](jenkins/task/nodejs/test.md)
     * [preview](jenkins/task/nodejs/preview.md)
     * [release](jenkins/task/nodejs/release.md)
  * [Task 實作以 Java + git 為例](jenkins/task/java_git/README.md)
     * [build](jenkins/task/java_git/build.md)
     * [test](jenkins/task/java_git/test.md)
     * [preview](jenkins/task/java_git/preview.md)
     * [release](jenkins/task/java_git/release.md)
  * [Task 實作以 Java + SVN 為例](jenkins/task/java_svn/README.md)
     * [專案組成](jenkins/task/java_svn/project.md)
     * [初始資料](jenkins/task/java_svn/inital.md)
     * [build](jenkins/task/java_svn/build.md)
     * [test](jenkins/task/java_svn/test.md)
     * [preview](jenkins/task/java_svn/preview.md)
     * [release](jenkins/task/java_svn/release.md)
  * Task 實作進階
     * [cron jobs test](jenkins/task/cron_test.md)
     * [pull request test](jenkins/task/pr_test.md)
     * [branch/fork preview](jenkins/task/branch_fork_preview.md)
     * [if test ok then preview](jenkins/task/if_test_ok_then_preview.md)
  * [搭配 docker 使用 Jenkins 協助測試](jenkins/withDocker/README.md)
     * [install](jenkins/withDocker/install.md)
     * [build](jenkins/withDocker/build.md)
     * [test](jenkins/withDocker/test.md)
     * [preview](jenkins/withDocker/preview.md)
     * [release](jenkins/withDocker/release.md)
  * [搭配 Jenkins 2.0 之 Pipeline 進行建置](jenkins/jenkins2/README.md)
     * [基礎練習](jenkins/jenkins2/pipeline/tutorial/README.md)
     * [使用 Pipeline 進行建置](jenkins/jenkins2/pipeline/build/README.md)
     * [使用 GitHub Organization 進行建置](jenkins/jenkins2/github-organization/README.md)
     * [使用 Multibranch Pipeline 進行建置](jenkins/jenkins2/multibranch-pipeline/README.md)

  * 自動化檢查與報表設置
    * [java doc 使用與報表產出設置](./jenkins/check/javadoc/README.md)
    * [Checkstyle 使用與報表產出設置](./jenkins/check/checkstyle/README.md)
    * [PMD(source code analyzer) 使用與報表產出設置](./jenkins/check/pmd/README.md)
    * [CPD(Copy/Paste Detector) 使用與報表產出設置](./jenkins/check/dry/cpd//README.md)
    * [Simian 使用與報表產出設置](./jenkins/check/dry/simian/README.md)
    * [FindBugs 使用與報表產出設置](./jenkins/check/findBugs/README.md)
  * 建置工具
    * maven
      * [Multi Module Project](./jenkins/maven/multi-app/README.md)

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

  - [Lesson 3: Docker Machine 的使用 (1 hour)](docker/machine/README.md)
    - [install](docker/machine/install/README.md)
    - [drive](docker/machine/drive/README.md)
    - [create](docker/machine/create/README.md)
    - [env](docker/machine/env/README.md)
    - [ls](docker/machine/ls/README.md)
    - [使用 docker-machine 連結已存在之遠端 docker engine](docker/machine/exist-remote-docker/README.md)
    - [upgrade](docker/machine/upgrade/README.md)
    - [rm](docker/machine/rm/README.md)

  - [Lesson 4: 善用 docker hub 上的 image (0.5 hour)](docker/hub/README.md)

    - [ubuntu](docker/hub/ubuntu/README.md)
    - [alpine](docker/hub/alpine/README.md)
    - [mysql](docker/hub/mysql/README.md)
    - [maven](docker/hub/maven/README.md)
    - [Node.js](docker/hub/nodejs/README.md)

  - Lab 601: 使用 docker 建置 java 開發環境 (1 hour)

    - [運行環境安裝](docker/project/java/env/README.md)
    - [進入 Container 進行建置](docker/project/java/env-docker-build/README.md)
    - [透過 Dockerfile 進行建置](docker/project/java/env-dockerfile/README.md)

  - Lab 602: 使用 docker 建置 Jenkins 服務 (1 hour)

    - [進入 Container 進行建置](docker/application/jenkins/build-docker/README.md)
    - [透過 Dockerfile 進行建置](docker/application/jenkins/build-dockerfile/README.md)

  - Lab 603: docker 之間溝通透過 depends_on(1 hour)
  - Lab 701: java 範例專案使用 docker 進行建置 (1 hour)

    - [範例專案](docker/project/java/repository/README.md)
    - [安裝](docker/project/java/mvn-install/README.md)
    - [測試](docker/project/java/mvn-test/README.md)
    - [運行](docker/project/java/mvn-run/README.md)
    - [打包](docker/project/java/mvn-package/README.md)

  - Lab 702: docker-compose
    - [run and up](docker/compose/run_up/README.md)
    - [其他指令](docker/compose/other_command/README.md)

  - Lab 703: java 範例專案使用 docker-compose 進行建置 (1 hour)

    - [練習：製作 dev mode service](docker/pratice/compose-dev-mode.md)
    - [範例專案](docker/project/java/repository/README.md)
    - [安裝](docker/project/java/compose-mvn-install/README.md)
    - [測試](docker/project/java/compose-mvn-test/README.md)
    - [運行](docker/project/java/compose-mvn-run/README.md)
    - [打包](docker/project/java/compose-mvn-package/README.md)

  - Lab 704: java 範例專案進行 production 並且搭配 jenkins (1 hour)

    - [production image 製作](docker/project/java/production-image-build/README.md)
    - [練習：docker production 發布流程](docker/pratice/production-image-publish.md)
    - [練習：使用 production image 運行專案](docker/pratice/production-image-run.md)
    - [練習：搭配 jenkins 建立 production deploy task](docker/pratice/jenkins-docker-prod-deploy-task.md)

  - [Lab 801: java jenkins 2.0 Pipeline 使用 Docker 進行專案建置 (1 hour)](docker/jnekins2/pipeline/build/README.md)

  - Lab 901: docker swarm

    -	[local network cluster](docker/swarm/local/README.md)
    - [overlay network cluster](docker/swarm/overlay/README.md)
- Slack
  - [github 整合](./slack/github/README.md)
  - [jenkins 整合](./slack/jenkins/README.md)
- Appendix

  - [vt-x amd-v 異常造成 VM 無法開啟](docker/troubleshooting/vt_x_amd_v_error/README.md)
  - [Ubuntu install docker](docker/install/ubuntu/README.md)
  - [Mac OS X install docker](docker/install/osx/README.md)
  - [docker 參考資料](docker/reference/README.md)
  - [git 參考資料](git/reference/README.md)
  - [docker 相關練習解答](docker/pratice/answer.md)
