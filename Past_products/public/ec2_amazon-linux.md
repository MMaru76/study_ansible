```
# yum --enablerepo=epel search ansible
Loaded plugins: priorities, update-motd, upgrade-helper
amzn-main                                                                                                                                                                            | 2.1 kB  00:00:00
amzn-updates                                                                                                                                                                         | 2.5 kB  00:00:00
epel/x86_64/metalink                                                                                                                                                                 | 6.4 kB  00:00:00
epel                                                                                                                                                                                 | 5.3 kB  00:00:00
(1/3): epel/x86_64/group_gz                                                                                                                                                          |  71 kB  00:00:00
(2/3): epel/x86_64/updateinfo                                                                                                                                                        | 788 kB  00:00:00
(3/3): epel/x86_64/primary_db                                                                                                                                                        | 6.1 MB  00:00:00
1065 packages excluded due to repository priority protections
=========================================================================================== N/S matched: ansible ===========================================================================================
ansible-doc.noarch : Documentation for Ansible
ansible-inventory-grapher.noarch : Creates graphs representing ansible inventory
ansible-lint.noarch : Best practices checker for Ansible
python2-ansible-tower-cli.noarch : A CLI tool for Ansible Tower
ansible.noarch : SSH-based configuration management, deployment, and task execution system

  Name and summary matches only, use "search all" for everything.
```

```
# yum --enablerepo=epel info ansible
Loaded plugins: priorities, update-motd, upgrade-helper
1065 packages excluded due to repository priority protections
Available Packages
Name        : ansible
Arch        : noarch
Version     : 2.6.17
Release     : 1.el6
Size        : 10 M
Repo        : epel/x86_64
Summary     : SSH-based configuration management, deployment, and task execution system
URL         : http://ansible.com
License     : GPLv3+
Description : Ansible is a radically simple model-driven configuration management,
            : multi-node deployment, and remote task execution system. Ansible works
            : over SSH and does not require any software or daemons to be installed
            : on remote nodes. Extension modules can be written in any language and
            : are transferred to managed machines automatically.
```

```
# yum --enablerepo=epel install ansible

~~~

Complete!
```

```
# ansible --version
ansible 2.6.17
  config file = /etc/ansible/ansible.cfg
  configured module search path = [u'/root/.ansible/plugins/modules', u'/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python2.6/site-packages/ansible
  executable location = /usr/bin/ansible
  python version = 2.6.9 (unknown, Nov  2 2017, 19:21:21) [GCC 4.8.5 20150623 (Red Hat 4.8.5-11)]
```