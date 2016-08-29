# Tomcatインストール
****
### CentOS7のTomcatインストール

  1. グループ、ユーザ作成

          groupadd tomcat
          useradd -g tomcat -d /home/tomcat -s /bin/bash tomcat

  1. ファイル転送  

    jdk (例：jdk-8u71-linux-x64.tar.gz)

    apache-tomcat (例：apache-tomcat-8.0.30.tar.gz)
  1. 解凍先フォルダ作成  
  ```
  cd /home/tomcat
  mkdir bin
  ```
  1. ファイル移動
  ```
  cp /home/vagrant/jdk-8u101-linux-x64.tar.gz  /home/tomcat/
  cp /home/vagrant/apache-tomcat-8.5.4.tar.gz /home/tomcat/
  ```
  1. ファイル解凍
  ```
  tar zxf /home/tomcat/apache-tomcat-8.5.4.tar.gz -C /home/tomcat/bin
  tar zxf /home/tomcat/jdk-8u101-linux-x64.tar.gz -C /home/tomcat/bin
  ```
  1. オーナー変更
  ```
  chown -R tomcat. /home/tomcat/bin/apache-tomcat-8.5.4
  chown -R tomcat. /home/tomcat/bin/jdk1.8.0_101
  ```
  1. サービスの定義ファイル作成 （CentOS7特有）
  ```
  vi /etc/systemd/system/tomcat.service
  ```
  tomcat.service内容
  ```
    [Unit]
    Description=Apache Tomcat 8.5 for tomcat
    After=network.target

    [Service]
    User=tomcat
    Group=tomcat
    Type=oneshot
    PIDFile=/home/tomcat/bin/apache-tomcat-8.5.4/tomcat.pid
    RemainAfterExit=yes

    EnvironmentFile=/etc/sysconfig/tomcat
    ExecStart=/home/tomcat/bin/apache-tomcat-8.5.4/bin/startup.sh
    ExecStop=/home/tomcat/bin/apache-tomcat-8.5.4/bin/shutdown.sh
    ExecReStart=/home/tomcat/bin/apache-tomcat-8.5.4/bin/shutdown.sh;/home/tomcat/bin/apache-tomcat-8.5.4/bin/startup.sh

    [Install]
    WantedBy=multi-user.target
  ```
  1. Java設定ファイル作成 （CentOS7特有）
  ```
  vi /etc/sysconfig/tomcat
  ```
  設定ファイルの内容
  ```
  JAVA_HOME="/home/tomcat/bin/jdk1.8.0_101/"
  JAVA_OPTS="-Djava.security.egd=file:/dev/./urandom"
  ```
  1. サービスの定義ファイルの権限変更
  ```
  chmod 755 /etc/systemd/system/tomcat.service
  ```
  1. サービス起動
  ```
  systemctl start tomcat
  systemctl enable tomcat
  systemctl stop tomcat
  systemctl disable tomcat
  ```
  1. サービス起動を確認

    http://XXX.XXX.XXX.XXX:8080/
