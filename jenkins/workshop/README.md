# Jenkins Quick Start

## 安裝提示

1. 安裝 Ubuntu Linux 16.04 LTS
2. 安裝 Java
   ```
   sudo apt-get install openjdk-8-jdk
   ```
3. 安裝 Jenkins
   ```
   wget -q -O - https://jenkins-ci.org/debian/jenkins-ci.org.key | sudo apt-key add -
   sudo sh -c 'echo deb http://pkg.jenkins-ci.org/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
   sudo apt-get update
   sudo apt-get install jenkins
   ```
4. 設定 Jenkins
   ```
   # /etc/default/jenkins
   HTTP_PORT=8080
   JAVA_ARGS="-Djava.awt.headless=true -Xmx1024m"
   ```
5. 設定 sudo 權限與免密碼
   ```
   # /etc/passwd
   jenkins:x:111:117:Jenkins,,,:/var/lib/jenkins:/bin/bash
   
   # /etc/sudoers
   %sudo   ALL=(ALL:ALL) NOPASSWD: ALL
   
   # /etc/group
   sudo:x:27:user,jenkins
   ```
6. 管理 Jenkins
   ```
   # Upgrade
   sudo apt-get update && sudo apt-get upgrade jenkins
   
   # Start, Restart, Stop
   sudo service jenkins start
   sudo service jenkins restart
   sudo service jenkins stop
   ```
