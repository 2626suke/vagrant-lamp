## 構成
|ソフトウェア|バージョン|
|:--|:-:|
|CentOS|6.5|
|Apache|2.2.15|
|PHP|5.6.9|
|MySQL|5.6.24|
|phpMyAdmin|4.4.7|
|Composer|1.0-dev|
|Xdebug|2.3.2|

## インストール方法
#### VirtulBoxのインストール
https://www.virtualbox.org/wiki/Downloads

#### Vagrantのインストール
http://www.vagrantup.com/downloads.html
```
vagrant -v
```

#### Vagrant設定ファイルのインストール
```
git clone https://github.com/2626suke/vagrant-lamp.git
```

## 使用法
#### 起動
```
vagrant up
```

#### 停止
```
vagrant halt
```

#### 破棄
```
vagrant destroy
```

