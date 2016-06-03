使用指令進行 plugin 安裝
========================

下面連結可以看到目前官方所有的 plugins

http://updates.jenkins-ci.org/download/plugins/

我們可以透過下列指令進行套件安裝

```
cd $JENKINS_HOME/plugins
curl -O http://updates.jenkins-ci.org/latest/plugins/cobertura.hpi
curl -O http://updates.jenkins-ci.org/latest/plugins/publish-over-ssh.hpi
curl -O http://updates.jenkins-ci.org/latest/plugins/git.hpi
curl -O http://updates.jenkins-ci.org/latest/plugins/config-file-provider.hpi
```
