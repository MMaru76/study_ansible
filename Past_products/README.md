# study_ansible

## setup

- 編集中
<!--
```
sudo yum -y install ansible
git clone git://github.com/ansible/ansible.git
cd ./ansible
make rpm
sudo rpm -Uvh ~/rpmbuild/ansible-*.noarch.rpm
``` -->

## Host

- Mac OS X_10.14.6_18G87

```
sudo launchctl limit maxfiles 1024 unlimited
sudo easy_install pip
sudo pip install ansible

ansible --version
  => ansible 2.8.4
```

- Amazon Linux (EC2)

```
yum --enablerepo=epel install ansible

ansible --version
  => ansible 2.6.17
```

- CentOS7

```
yum -y install ansible

ansible --version
  => ansible 2.4.2.0
```

## Guest

- CentOS系

```
sudo yum -y install python-simplejson
```

- Debian(未検証)

```
sudo apt-get -y install python-simplejson
```

- ALL Instance(未検証)

```
ansible all -m raw -a 'yum -y install python-simplejson'
```

## 基本的な三種類の設定ファイル

1. inventory ファイル
2. playbook ファイル
3. ansible.cfg ファイル

## コマンドオプションの解説

- -k
  - 対話形式でパスワード入力
- -a "コマンド"
  - 指定のコマンドを実行
    - 例:ansible all -a "yum -y update"
- -m
  - モジュール
    - 例:ansible all -m ping
    - 例:ansible all -m command -a "yum -y update"
- --become-user="ユーザー名"
  - root以外のユーザー名
- --become-method="sudo"
  - 昇格方法を選択
    - sudo/su/pbrun/pfexec/runas


## 基本的な実行コマンド

### ホストの各種指定方法

- 特定のサブドメインに対して
  - ans.tabiya.local
- 特定のサブドメインのホストすべて
  - ans*.tabiya.local
- ans1からans50までに対して
  - ans[01:50].tabiya.local
- ans か dns(or 指定)
  - ans:dns
- [編集中]not指定
- [編集中]and指定
- [編集中]複数指定

### ping の確認方法

対象のホスト達が生存してるかの確認を行う｡

- hostsに記述されているホスト全部に対してping送信
```
ansible all -m ping
```

- target_serversのグループに対してpingを送信
```
ansible target_servers -m ping
```

---

### ホストのコマンドを実行方法

特定のホストまたは､特定のグループ群み対して実行｡

- hostsに記述されているホスト全部に対して〇〇コマンドを実行

```
ansible target_servers -m command -a "yum -y update"
```

- target_serversのグループに対して〇〇コマンドを実行

```
ansible all -m command -a "yum -y update"
```

---

### rootで接続出来ない時に使うコマンドの実行方法

user名と昇格方法に対しては""(ダブルクオーテーション)は任意

```
ansible all -k -m command -a "yum -y update" --become-user="maru" --become-method="sudo"
```

```
ansible ans -m command -a "yum -y update" --become-user=maru --become-method=sudo
```
