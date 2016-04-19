# Summary

- [Docker](docker/README.md)

- [Meet Docker](docker/000-intro/README.md)

  - [What is Docker](docker/000-intro/what/README.md)
  - [Docker vs VMs](docker/000-intro/compare/README.md)
  - [Why Docker](docker/000-intro/why/README.md)
  - [Image](docker/000-intro/image/README.md)
  - [Container](docker/000-intro/container/README.md)
  - [Repository](docker/000-intro/repository/README.md)
  - [Registry](docker/000-intro/registry/README.md)

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

- Lab 103: Data Volumes

- [Lab 104: Registry](docker/basic/104-registry/README.md)

  - [distribution private](docker/basic/104-registry/distribution-private/README.md)
  - [distribution public](docker/basic/104-registry/distribution-public/README.md)

- [Lesson 3: Docker Machine 的使用 (1 hour)](docker/machine/README.md)

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

- Lesson 5: 範例專案建置流程說明 (0.5 hour)

- Lab 601: 使用 docker 建置 java 開發環境 (1 hour)

  - [運行環境安裝](docker/project/java/env/README.md)
  - [進入 Container 進行建置](docker/project/java/env-docker-build/README.md)
  - [透過 Dockerfile 進行建置](docker/project/java/env-dockerfile/README.md)

- Lab 602: 使用 docker 建置 Node.js 開發環境 (1 hour)

  - [運行環境安裝](docker/project/nodejs/env/README.md)
  - [進入 Container 進行建置](docker/project/nodejs/env-docker-build/README.md)
  - [透過 Dockerfile 進行建置](docker/project/nodejs/env-dockerfile/README.md)

- Lab 603: 使用 docker 建置 Jenkins 服務 (1 hour)

  - [進入 Container 進行建置](docker/application/jenkins/build-docker/README.md)
  - [透過 Dockerfile 進行建置](docker/application/jenkins/build-dockerfile/README.md)

- Lab 701: java 範例專案使用 docker 進行建置 (1 hour)

  - [範例專案](docker/project/java/repository/README.md)
  - [安裝](docker/project/java/mvn-install/README.md)
  - [測試](docker/project/java/mvn-test/README.md)
  - [運行](docker/project/java/mvn-run/README.md)
  - [打包](docker/project/java/mvn-package/README.md)

- Lab 702: Node.js 範例專案使用 docker 進行建置 (1 hour)

  - [範例專案](docker/project/nodejs/repository/README.md)
  - 測試
  - 運行
  - 打包

- Lab 703: java 範例專案使用 docker-compose 進行建置 (1 hour)

  - [範例專案](docker/project/java/repository/README.md)
  - [安裝](docker/project/java/compose-mvn-install/README.md)
  - [測試](docker/project/java/compose-mvn-test/README.md)
  - [運行](docker/project/java/compose-mvn-run/README.md)
  - [打包](docker/project/java/compose-mvn-package/README.md)

- Lesson 9: 範例專案進行 production image 製作 (0.5 hour)

- Lesson 10: docker-swarm 基礎範例 (0.5 hour)

- Lesson 11: docker network 操作指令 (1 hour)

- Lesson 12: docker-swarm 搭配 network (1 hour)

- Appendix: 環境安裝建置

  - AgileWorks
  - [Ubuntu](docker/install/ubuntu/README.md)
  - [Mac OS X](docker/install/osx/README.md)
  - Windows

- [Appendix: 參考資料](docker/reference/README.md)
