# CentOS7 Ruby base vagrant image
## Overview  
Ruby開発用local環境

## Requirements
* Vagrant `1.9.0` or higher
* Ansible `2.2.0` or higher
* vagrant-vbguest

## Installation
### Tools install
* Vagrantのインストール  
  [https://www.vagrantup.com/downloads.html]("https://www.vagrantup.com/downloads.html")
* VirtualBoxのインストール  
  [https://www.virtualbox.org/wiki/Downloads]("https://www.virtualbox.org/wiki/Downloads")
* Ansibleのインストール  
```bash
$ brew install ansible
```

### Vagrant installation
```bash
# vagrant-vbguestをインストールする
$ vagrant plugin install vagrant-vbguest

# /HOST APPLICATION PATHをApplicationのパスに変更する
$ vim Vagrantfile
$ rm -rf roles/*
$ ansible-galaxy install -r requirements.yml -p roles
$ vagrant up
```

## Update vagrant
vagrantの更新が行われた際のオペレーション
```bash
$ git pull
$ rm -rf roles/galaxy-*
$ ansible-galaxy install -r requirements.yml -p roles
$ vagrant up --provision
```

## Errors
* mountに失敗する
```bash
# vagrantが起動している状態でホスト内で実行
$ vagrant vbguest --do install
$ vagrant reload
```

## Access to services
* nginx  
[http://localhost:10080]("http://localhost:10080")
* mailcatcher  
[http://localhost:11080]("http://localhost:11080")
* rails  
[http://localhost:13000]("http://localhost:13000")
* minio  
[http://localhost:19000]("http://localhost:19000")
