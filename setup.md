# 初期設定について

## 条件&注意

- 特定のサービス群に入っている事
- CentOS7で実行可能
- 起動したばかりの際に使用
- 実行時は､実行ログは出力されない

パスワード有り

```
ansible グループ群 -k -m shell -a "systemctl stop firewalld ; systemctl disable firewalld; sed -i -e "s/enforcing/disabled/g" /etc/selinux/config ; yum -y update ; yum -y groupinstall base ; reboot"
```

パスワード無し

```
ansible グループ群 -m shell -a "systemctl stop firewalld ; systemctl disable firewalld ; sed -i -e "s/enforcing/disabled/g" /etc/selinux/config ; sed -i -e '$a DNS2="8.8.8.8"' /etc/sysconfig/network-scripts/ifcfg-ens192 ; systemctl restart network ; yum -y update ; yum -y groupinstall base ; shutdown -h"
```

上記のコマンドを実行する事によって､対象のグループホストに対して特定のコマンドを実行する事が出来ます｡


# 中身のコマンドについて
```
//ファイアーウォールの停止/自動停止
# systemctl stop firewalld ; systemctl disable firewalld

// SELinuxの無効
# sed -i -e "s/enforcing/disabled/g" /etc/selinux/config

// 最新/便利な物の導入/再起動
# yum -y update ; yum -y groupinstall base ; reboot
```

DNS2="8.8.8.8"
vim /etc/sysconfig/network-scripts/ifcfg-ens192