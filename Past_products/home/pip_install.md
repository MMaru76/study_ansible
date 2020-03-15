## pip install

```
yum -y install epel-release
yum -y groupinstall -y "Development Tools"
yum -y install python-devel sshpass
curl -kL "https://bootstrap.pypa.io/get-pip.py" | sudo python
pip install virtualenv
cd $HOME/
virtualenv venv
source $HOME/venv/bin/activate
(venv) pip install ansible
(venv) ansible --version
```

下記のコマンドで virtualenv モードに入る

```
source $HOME/venv/bin/activate
```