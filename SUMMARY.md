# Summary

- 上課須知

  - [事前安裝：自備筆電](prepare/laptop.md)
  - [事前安裝：電腦教室](prepare/pc.md)
  - [事前安裝：VirtualBox 映像檔匯入](prepare/vm-import.md)

  * [Git 基礎]()
    * [Git 是什麼？](./git/foundation/what.md)
    * [為什麼我們需要 Git](./git/foundation/why.md)
    * [初始化專案 init](./git/command/init.md)
    * [設定檔 config](./git/command/config.md)
    * [練習題：init](./git/practice/init.md)
    * [觀念講解：索引](./git/foundation/index.md)
    * [觀念講解：認識 Git 物件](./git/foundation/object.md)
  * [Git 之 CRUD]()
    * [工作區、暫存區、儲存庫](./git/foundation/space.md)
    * [狀態 status](./git/command/status.md)
    * [新增 add](./git/command/add.md)
    * [送交 commit](./git/command/commit.md)
    * [練習題：commit](./git/practice/commit.md)
    * [檢視 log / show](./git/command/log.md)
    * [比對差異 diff](./git/command/diff.md)
    * [刪除 rm](./git/command/rm.md)
    * [練習題：rm](./git/practice/rm.md)
    * [重新命名 mv](./git/command/mv.md)
  * [觀念講解： Git Flow]()
    * [整體概念](./git/git-flow/README.md)
    * [master 分支](./git/git-flow/master.md)
    * [feature 分支](./git/git-flow/feature.md)
    * [hotfix 分支](./git/git-flow/hotfix.md)
  * [分支 branch]()
    * [分支 branch CRUD](./git/command/branch.md)
    * [切換 checkout](./git/command/checkout.md)
    * [練習題：checkout](./git/practice/checkout.md)
    * [練習題：branch](./git/practice/branch.md)
    * [合併 merge](./git/command/merge.md)
    * [觀念解說：解決衝突](./git/foundation/conflict.md)
    * [練習題：conflict 解決衝突](./git/practice/conflict.md)
    * [暫存 stash](./git/command/stash.md)
    * [練習題：stash](./git/practice/stash.md)
  * [修改送交]()
    * [還原 reset](./git/command/reset.md)
    * [練習題：reset](./git/practice/reset.md)
    * [資料還原 revert](./git/command/revert.md)
    * [重新指定位置 rebase](./git/command/rebase.md)
    * [練習題：rebase](./git/practice/rebase.md)
    * [觀念講解：reset vs revert](./git/foundation/reset-vs-revert.md)
  * [遠端協作]()
    * [容器](./git/foundation/container.md)
    * [remote](./git/command/remote.md)
    * [複製 clone](./git/command/clone.md)
    * [拉 pull](./git/command/pull.md)
    * [更新 fetch](./git/command/fetch.md)
    * [練習題：fetch](./git/practice/fetch.md)
    * [部署 push](./git/command/push.md)
    * [練習題：push](./git/practice/push.md)
    * [標籤 tag](./git/command/tag.md)
    * [練習題：發佈 tag](./git/practice/tag.md)
  * [Github](./git/github/README.md)
    * [issue](./git/github/issue.md)
    * [clone](./git/github/clone.md)
    * [fork](./git/github/fork.md)
    * [pull request](./git/github/pr.md)
    * [練習題：操作 Github](./git/practice/github.md)
  * [補充]()
    * [reflog](./git/command/reflog.md)
    * [blame](./git/command/blame.md)
    * [grep](./git/command/grep.md)
    * [tig](./git/mise/tig.md)
    * [實用小技巧](./git/tips.md)
    * [更多資源](./git/resource.md) -->



  - [初始 Git 專案](git/start/README.md)
  - [clone 已建立之遠端專案](git/clone/README.md)
  - [log 使用](git/log/README.md)
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
  
  - [編修衝突](git/conflict/README.md)  
  - [tag 使用](git/tag/README.md)
  - [什麼是 Git Flow](git/flow/README.md)
  

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
     * [Lab 103](jenkins/workshop/lab104.md)
     
  * [CI flow 簡介](jenkins/task/flow.md)
  * [持續整合實作以 Java + git 為例](jenkins/task/java_git/README.md)
    * [Lab 進行方式說明](jenkins/task/README.md)
    * Lab 201 建置 
      * [build-package](jenkins/task/java_git/build.md)
      * [build-archive](jenkins/common/build-archive.md)
    * Lab 202 測試
      * [單元測試 JUnit ](jenkins/common/test-report.md)
      * [測試覆蓋率 Cobertura](jenkins/plugin/cobertura.md)
    * Lab 203 部署
      * [ssh 遠端連線設置](jenkins/setup/ssh.md)
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

  <!-- * 設定
     * [環境變數](jenkins/setup/env.md)
     * [ssh 與 scp](jenkins/setup/ssh.md) -->

  * 進階設定
     * [security](jenkins/setup/security.md)
     * [timezone](jenkins/setup/timezone.md)
     * [master/slave](jenkins/setup/master-slave.md)


  * Q & A
     * [一般問題](jenkins/QA/general.md)
     * [JAVA](jenkins/QA/java.md)

- Appendix

  - [vt-x amd-v 異常造成 VM 無法開啟](docker/troubleshooting/vt_x_amd_v_error/README.md)
  - [git 參考資料](git/reference/README.md)