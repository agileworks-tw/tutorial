# Summary

- 上課須知

  - [相關服務事前註冊](prepare/service-signup.md)
  - [事前安裝：自備筆電](prepare/laptop.md)
  - [事前安裝：電腦教室](prepare/pc.md)

- TDD(測試驅動開發方式)
  - Java
    - [JUnit 基礎](./tdd/java/junit4/basic/README.md)
    - [JUnit 與 Maven](./tdd/java/junit4/maven/README.md)
    - [Assertions](./tdd/java/junit4/assertions/README.md)
    - [Test Fixtures](./tdd/java/junit4/test-fixture/README.md)
    - [略過 test](./tdd/java/junit4/test-fixture/README.md)
    - [Junit 測試 API](./tdd/java/junit4/api-test/README.md)
    - [JUnit Test Suite](./tdd/java/junit4/suite/README.md)

- Jenkins

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
     * [master/slave](jenkins/setup/master-slave.md)
  * Jenkins CI 常用功能
     * [build archive](jenkins/common/build-archive.md)
     * [執行 Shell Script](jenkins/common/shell.md)
     * [Jenkins API 使用簡介](jenkins/common/api.md)
     * [Plugin 安裝](jenkins/common/plugin.md)
     * [JUnit 報表](jenkins/common/test-report.md)
     * [Script Console](jenkins/common/script-console.md)
  * [常用 plugin 介紹](jenkins/plugin/README.md)
     * [Config File Provider](jenkins/plugin/config-file-provider.md)
     * [Cobertura](jenkins/plugin/cobertura.md)
     * [使用指令安裝常用套件](jenkins/plugin/install_use_command.md)
  * [CI flow 簡介](jenkins/task/flow.md)
  * [Task 實作以 Java + git 為例](jenkins/task/java_git/README.md)
     * [build](jenkins/task/java_git/build.md)
     * [test](jenkins/task/java_git/test.md)
     * [preview](jenkins/task/java_git/preview.md)
     * [release](jenkins/task/java_git/release.md)
  * Task 實作進階
     * [cron jobs test](jenkins/task/cron_test.md)
     * [if test ok then preview](jenkins/task/if_test_ok_then_preview.md)
  * [搭配 Jenkins 2.0 之 Pipeline 進行建置](jenkins/jenkins2/README.md)
     * [基礎練習](jenkins/jenkins2/pipeline/tutorial/README.md)
     * [使用 Pipeline 進行建置](jenkins/jenkins2/pipeline/build/README.md)
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

- Appendix

  - [vt-x amd-v 異常造成 VM 無法開啟](docker/troubleshooting/vt_x_amd_v_error/README.md)
  - [Ubuntu install docker](docker/install/ubuntu/README.md)
  - [Mac OS X install docker](docker/install/osx/README.md)
  - [docker 參考資料](docker/reference/README.md)
  - [git 參考資料](git/reference/README.md)
  - [docker 相關練習解答](docker/pratice/answer.md)
