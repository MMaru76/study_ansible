# ゲスト環境
- 192.168.2.21 = app-1e.tabiya.local

```
[maru@dns ~]$ ansible-playbook -i wp_ansible/inventory.ini wp_ansible/test_playbook.yml 
ERROR! Empty playbook, nothing to do
[maru@dns ~]$ cd wp_ansible/
[maru@dns wp_ansible]$ ansible-playbook -i inventory.ini test_playbook.yml 

PLAY [apps] *********************************************************************************************

TASK [Gathering Facts] **********************************************************************************
The authenticity of host '192.168.2.21 (192.168.2.21)' can't be established.
ECDSA key fingerprint is SHA256:WTI7gk7hOzSMY1tL0AzX5+Dk9P8GeOpPlmn2NYagwbQ.
ECDSA key fingerprint is MD5:c0:3f:02:32:74:a8:15:f1:01:ff:87:4e:7a:a5:fb:ae.
Are you sure you want to continue connecting (yes/no)? yes
fatal: [app-2e]: UNREACHABLE! => {"changed": false, "msg": "Failed to connect to the host via ssh: ssh: connect to host 192.168.2.22 port 22: No route to host", "unreachable": true}
ok: [app-1e]

TASK [create directory] *********************************************************************************
changed: [app-1e]

TASK [copy file] ****************************************************************************************
changed: [app-1e]

PLAY RECAP **********************************************************************************************
app-1e                     : ok=3    changed=2    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
app-2e                     : ok=0    changed=0    unreachable=1    failed=0    skipped=0    rescued=0    ignored=0   
```