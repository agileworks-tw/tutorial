# Summary

- 上課須知

  - [相關服務事前註冊](prepare/service-signup.md)
  - [事前安裝：自備筆電](prepare/laptop.md)
  - [事前安裝：電腦教室](prepare/pc.md)
  - [VirtualBox 映像檔匯入](prepare/after-import.md)  

- gitlab
  * [使用者驗證設置](gitlab/user-add-ssh-key/README.md)

- Jenkins
  * [Introduction](jenkins/README.md)
  * [Quick Start](jenkins/workshop/README.md)
     * [Lab 101](jenkins/workshop/lab101.md)
     * [Lab 102](jenkins/workshop/lab103.md)

  * 設定
     * [ssh](jenkins/setup/ssh.md)
     * [security](jenkins/setup/security.md)
     * [master/slave](jenkins/setup/master-slave.md)

  * [CI flow 簡介](jenkins/task/flow.md)
  * [Task 實作以 Java + git 為例](jenkins/task/java_git/README.md)
     * [build](jenkins/task/java_git/build.md)
     * [test](jenkins/task/java_git/test.md)
     * [preview](jenkins/task/java_git/preview.md)
     * [release](jenkins/task/java_git/release.md)
  * [搭配 Jenkins 2.0 之 Pipeline 進行建置](jenkins/jenkins2/README.md)
     * [使用 Pipeline 進行建置](jenkins/jenkins2/pipeline/build/README.md)
     * [使用 Multibranch Pipeline 進行建置](jenkins/jenkins2/multibranch-pipeline/README.md)

  * 自動化檢查與報表設置
    * [Jenkins Warnings Next Generation Plugin](./jenkins/check/warnings-ng/README.md)
    * [java doc 使用與報表產出設置](./jenkins/check/javadoc/README.md)
    * [Checkstyle 使用與報表產出設置](./jenkins/check/checkstyle/README.md)
    * [PMD(source code analyzer) 使用與報表產出設置](./jenkins/check/pmd/README.md)
    * [CPD(Copy/Paste Detector) 使用與報表產出設置](./jenkins/check/dry/cpd//README.md)
    * [FindBugs 使用與報表產出設置](./jenkins/check/findBugs/README.md)

- Appendix
  - [vt-x amd-v 異常造成 VM 無法開啟](docker/troubleshooting/vt_x_amd_v_error/README.md)
