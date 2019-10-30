systemctl stop firewalld ; systemctl disable firewalld; sed -i -e "s/enforcing/disabled/g" /etc/selinux/config ; yum -y update ; yum -y groupinstall base ; poweroff

ssh-copy-id -o StrictHostKeyChecking=no -i ~/.ssh/鍵名 対象インスタンス