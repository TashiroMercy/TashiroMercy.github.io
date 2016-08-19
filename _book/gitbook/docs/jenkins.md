# Jenkinsメモ
Vargrantを使用した手順
****
* Box
```Java
config.vm.box = "wgarcia/centos65-jenkins"
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
