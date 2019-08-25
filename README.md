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

## Guest

- CentOS

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