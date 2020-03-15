# Mac Ansible Setup方法

```
$ sw_vers
ProductName:	Mac OS X
ProductVersion:	10.14.6
BuildVersion:	18G87
```

```
$ python --version
Python 3.7.4
```

```
$ sudo launchctl limit maxfiles 1024 unlimited
Password:
```

```
$ sudo launchctl limit maxfiles
	maxfiles    1024           10240
```

```
$ sudo easy_install pip
Searching for pip
Best match: pip 19.0.3
Adding pip 19.0.3 to easy-install.pth file
Installing pip script to /usr/local/var/pyenv/versions/3.7.4/bin
Installing pip3 script to /usr/local/var/pyenv/versions/3.7.4/bin
Installing pip3.7 script to /usr/local/var/pyenv/versions/3.7.4/bin

Using /usr/local/var/pyenv/versions/3.7.4/lib/python3.7/site-packages
Processing dependencies for pip
Finished processing dependencies for pip
```

```
$ sudo pip install ansible
The directory '/Users/maruchan76/Library/Caches/pip/http' or its parent directory is not owned by the current user and the cache has been disabled. Please check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
The directory '/Users/maruchan76/Library/Caches/pip' or its parent directory is not owned by the current user and caching wheels has been disabled. check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
Collecting ansible
  Downloading https://files.pythonhosted.org/packages/93/cd/914c5f323b705afc53e521afe591490e5eb0bf118ec144547eb6cf84a87c/ansible-2.8.4.tar.gz (14.3MB)
    100% |████████████████████████████████| 14.4MB 5.3MB/s
Collecting jinja2 (from ansible)
  Downloading https://files.pythonhosted.org/packages/1d/e7/fd8b501e7a6dfe492a433deb7b9d833d39ca74916fa8bc63dd1a4947a671/Jinja2-2.10.1-py2.py3-none-any.whl (124kB)
    100% |████████████████████████████████| 133kB 33.6MB/s
Collecting PyYAML (from ansible)
  Downloading https://files.pythonhosted.org/packages/e3/e8/b3212641ee2718d556df0f23f78de8303f068fe29cdaa7a91018849582fe/PyYAML-5.1.2.tar.gz (265kB)
    100% |████████████████████████████████| 266kB 32.0MB/s
Collecting cryptography (from ansible)
  Downloading https://files.pythonhosted.org/packages/63/4e/57b7a6bd98906872fcd2531e74b532de2abe17d675a5cf171931fcb4a9e8/cryptography-2.7-cp34-abi3-macosx_10_6_intel.whl (1.6MB)
    100% |████████████████████████████████| 1.6MB 17.6MB/s
Collecting MarkupSafe>=0.23 (from jinja2->ansible)
  Downloading https://files.pythonhosted.org/packages/ce/c6/f000f1af136ef74e4a95e33785921c73595c5390403f102e9b231b065b7a/MarkupSafe-1.1.1-cp37-cp37m-macosx_10_6_intel.whl
Collecting six>=1.4.1 (from cryptography->ansible)
  Downloading https://files.pythonhosted.org/packages/73/fb/00a976f728d0d1fecfe898238ce23f502a721c0ac0ecfedb80e0d88c64e9/six-1.12.0-py2.py3-none-any.whl
Collecting cffi!=1.11.3,>=1.8 (from cryptography->ansible)
  Downloading https://files.pythonhosted.org/packages/f0/48/5aa4ea664eba26dd5142558d04762f5065c02220b4665b3f7eecb9bb614e/cffi-1.12.3-cp37-cp37m-macosx_10_9_x86_64.whl (169kB)
    100% |████████████████████████████████| 174kB 25.9MB/s
Collecting asn1crypto>=0.21.0 (from cryptography->ansible)
  Downloading https://files.pythonhosted.org/packages/ea/cd/35485615f45f30a510576f1a56d1e0a7ad7bd8ab5ed7cdc600ef7cd06222/asn1crypto-0.24.0-py2.py3-none-any.whl (101kB)
    100% |████████████████████████████████| 102kB 25.6MB/s
Collecting pycparser (from cffi!=1.11.3,>=1.8->cryptography->ansible)
  Downloading https://files.pythonhosted.org/packages/68/9e/49196946aee219aead1290e00d1e7fdeab8567783e83e1b9ab5585e6206a/pycparser-2.19.tar.gz (158kB)
    100% |████████████████████████████████| 163kB 29.5MB/s
Installing collected packages: MarkupSafe, jinja2, PyYAML, six, pycparser, cffi, asn1crypto, cryptography, ansible
  Running setup.py install for PyYAML ... done
  Running setup.py install for pycparser ... done
  Running setup.py install for ansible ... done
Successfully installed MarkupSafe-1.1.1 PyYAML-5.1.2 ansible-2.8.4 asn1crypto-0.24.0 cffi-1.12.3 cryptography-2.7 jinja2-2.10.1 pycparser-2.19 six-1.12.0
You are using pip version 19.0.3, however version 19.2.2 is available.
You should consider upgrading via the 'pip install --upgrade pip' command.
```

```
$ ansible --version
ansible 2.8.4
  config file = None
  configured module search path = ['/Users/maruchan76/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/local/var/pyenv/versions/3.7.4/lib/python3.7/site-packages/ansible
  executable location = /usr/local/var/pyenv/versions/3.7.4/bin/ansible
  python version = 3.7.4 (default, Aug 13 2019, 19:03:33) [Clang 10.0.1 (clang-1001.0.46.4)]
```

