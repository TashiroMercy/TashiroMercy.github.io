# Jenkinsインストールメモ
Vargrantを使用した手順
****
* Vargrant Box
```Java
config.vm.box = "wgarcia/centos65-jenkins"
```
* Vagrantfile 変更箇所（コメント解除）
```Spinx
config.vm.network "private_network", ip: "192.168.33.15"
config.vm.provider "virtualbox" do |vb|
  # Display the VirtualBox GUI when booting the machine
  vb.gui = true

  # Customize the amount of memory on the VM:
  vb.memory = "1024"
end
```
* 必要なパッケージのインストール
```
yum -y install httpd wget
```
* jdk確認
```
rpm -qa | grep jdk
```
* jdk削除
```
yum remove java-1.8.0-openjdk-1.8.0.101-3.b13.el7_2.x86_64
```
* jdkインストール(ダウンロード→転送後)
```
rpm -ivh jdk-8u101-linux-x64.rpm
```
* jenkinsの yum リポジトリを追加
```
wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat/jenkins.repo
```

* RPMパッケージの公開鍵をインポート
```
rpm --import http://pkg.jenkins-ci.org/redhat/jenkins-ci.org.key
```
* jenkins のインストール
```
yum -y install jenkins
```
* /etc/sysconfig/jenkins の編集内容（変更箇所のみ）
  * HTTP ポートの無効化(JENKINS_PORT)：
  * AJPポート変更(JENKINS_AJP_PORT)：
  * オプション変更（ProcessTreeKillerの無効+Timezoneの設定）JENKINS_JAVA_OPTIONS：
  * コンテキストパスの設定(JENKINS_ARGS)：
```
JENKINS_PORT="-1"
JENKINS_AJP_PORT="8109"
JENKINS_JAVA_OPTIONS="-Djava.awt.headless=true -Dhudson.util.ProcessTree.disable=true -Dorg.apache.commons.jelly.tags.fmt.timeZone=Asia/Tokyo -DjavaHome=/usr/java/default"
JENKINS_ARGS="--prefix=/jenkins"
```
* リバースプロキシの設定(Apache -> Jenkins)

  ※jenkins.conf新規作成
```
vi /etc/httpd/conf.d/jenkins.conf
```
```
ProxyPass           /jenkins ajp://localhost:8109/jenkins nocanon
ProxyPassReverse    /jenkins ajp://localhost:8109/jenkins
ProxyRequests       Off
AllowEncodedSlashes On
<Proxy "ajp://localhost:8109/jenkins">
  Order deny,allow
  Allow from all
</Proxy>
```
* firewall の設定
```
firewall-cmd --permanent --zone=public --add-service=http
firewall-cmd --permanent --zone=public --add-service=https
firewall-cmd --reload
```

* selinux の設定：
```
vi /etc/selinux/config
```
```
SELINUX=disabled
```
* 再起動もしくは selinux を一時的に無効化
```
setenforce 0
```
* サービスの起動と自動起動設定
```
service jenkins start
service httpd start
chkconfig jenkins on
chkconfig httpd on
```
* ブラウザで起動確認：

  http://XXX.XXX.XXX.XXX/jenkins
