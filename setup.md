//ファイアーウォールの停止/自動停止
# systemctl stop firewalld ; systemctl disable firewalld

ansible oreo -k -m shell -a "systemctl stop firewalld ; systemctl disable firewalld; sed -i -e "s/enforcing/disabled/g" /etc/selinux/config ; yum -y update ; yum -y groupinstall base ; reboot"

// SELinuxの無効
# sed -i -e "s/enforcing/disabled/g" /etc/selinux/config

// 最新/便利な物の導入/再起動
# yum -y update ; yum -y groupinstall base ; reboot