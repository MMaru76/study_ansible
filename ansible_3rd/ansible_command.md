# ホストサーバーのセットアップ

全て一般ユーザーで作業(共通ユーザー可)

## 基本的なインストール方法

```bash
$ sudo yum -y install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
$ sudo yum -y install ansible
```

## バージョン

```bash
$ ansible --version
=======================
ansible 2.8.5
  config file = /etc/ansible/ansible.cfg
  configured module search path = [u'/root/.ansible/plugins/modules', u'/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python2.7/site-packages/ansible
  executable location = /usr/bin/ansible
  python version = 2.7.5 (default, Aug  7 2019, 00:51:29) [GCC 4.8.5 20150623 (Red Hat 4.8.5-39)]
```

## 作業ディレクトリの作成

```bash
$ mkdir -vp effective_ansible/sec2
```

## ansible.cfg の設定

```bash
$ vim .ansible.cfg
=======================
[default]

forks = 15
log_path = $HOME/.ansible/ansible.log
host_key_checking = False
gathering = smart
```

## ansible コマンドの実行01

```bash
$ vim effective_ansible/sec2/inventory.ini
=======================
[test_sv]
localhost
=======================

$ ansible -i inventory.ini test_sv -m ping
=======================
localhost | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    },
    "changed": false,
    "ping": "pong"
}
```

## ansible コマンドの実行02

```bash
$ ansible -i inventory.ini test_sv -m file -a 'path=$HOME/test.txt state=touch mode=0644'
=======================
localhost | CHANGED => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    },
    "changed": true,
    "dest": "/home/maru/test.txt",
    "gid": 1000,
    "group": "maru",
    "mode": "0644",
    "owner": "maru",
    "size": 0,
    "state": "file",
    "uid": 1000
}
=======================

$ ll /home/maru/
合計 0
drwxrwxr-x 3 maru maru 18 10月 30 22:27 effective_ansible
-rw-r--r-- 1 maru maru  0 10月 30 23:03 test.txt
```

## ansible コマンドの実行02

- -b オプション
  - root権限が必要なものは､｢-b｣(become)オプション
- -K オプション
  - 検索中

```bash
$ ansible -i inventory.ini test_sv -m user -K -b -a 'user=user01 groups="wheel" append=yes comment="Test User01"'
=======================
BECOME password:(パスワード入力)
localhost | CHANGED => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    },
    "changed": true,
    "comment": "Test User01",
    "create_home": true,
    "group": 1001,
    "groups": "wheel",
    "home": "/home/user01",
    "name": "user01",
    "shell": "/bin/bash",
    "state": "present",
    "system": false,
    "uid": 1001
}
=======================

$ id user01
uid=1001(user01) gid=1001(user01) groups=1001(user01),10(wheel)
```

## 作成物の削除

```bash
$ ansible -i inventory.ini test_sv -m file -a 'path=$HOME/test.txt state=absent'
$ ansible -i inventory.ini test_sv -m user -K -b -a 'user=user01 state=absent'
```