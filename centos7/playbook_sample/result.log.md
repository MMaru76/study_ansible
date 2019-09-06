# アクセスページ

URL : http://test2.tabiya.local:8080/

[![Image from Gyazo](https://i.gyazo.com/94f82b8839b2b4648a7175ce9a355a47.png)](https://gyazo.com/94f82b8839b2b4648a7175ce9a355a47)

# 実行結果

```
[root@home ~]# ansible-playbook plyabook_sample.yml

PLAY [oreo] ********************************************************************

TASK [Gathering Facts] *********************************************************
ok: [test1.tabiya.local]
ok: [test2.tabiya.local]
fatal: [test3.tabiya.local]: UNREACHABLE! => {"changed": false, "msg": "Failed to connect to the host via ssh: ssh: connect to host test3.tabiya.local port 22: No route to host\r\n", "unreachable": true}
fatal: [test5.tabiya.local]: UNREACHABLE! => {"changed": false, "msg": "Failed to connect to the host via ssh: ssh: connect to host test5.tabiya.local port 22: No route to host\r\n", "unreachable": true}
fatal: [test4.tabiya.local]: UNREACHABLE! => {"changed": false, "msg": "Failed to connect to the host via ssh: ssh: connect to host test4.tabiya.local port 22: No route to host\r\n", "unreachable": true}

TASK [ins_httpd : httpd is installed dayo] *************************************
changed: [test1.tabiya.local] => (item=[u'httpd'])
changed: [test2.tabiya.local] => (item=[u'httpd'])

TASK [ins_httpd : edit http.conf] **********************************************
changed: [test1.tabiya.local] => (item={u'regexp': u'^#ServerName', u'line': u'ServerName test1.tabiya.local:8080'})
changed: [test2.tabiya.local] => (item={u'regexp': u'^#ServerName', u'line': u'ServerName test2.tabiya.local:8080'})
changed: [test1.tabiya.local] => (item={u'regexp': u'^Listen 80', u'line': u'Listen 8080'})
changed: [test2.tabiya.local] => (item={u'regexp': u'^Listen 80', u'line': u'Listen 8080'})

TASK [ins_httpd : httpd is running and enabled] ********************************
changed: [test1.tabiya.local]
changed: [test2.tabiya.local]

TASK [ins_httpd : put index.html] **********************************************
changed: [test1.tabiya.local]
changed: [test2.tabiya.local]
	to retry, use: --limit @/root/plyabook_sample.retry

PLAY RECAP *********************************************************************
test1.tabiya.local         : ok=5    changed=4    unreachable=0    failed=0
test2.tabiya.local         : ok=5    changed=4    unreachable=0    failed=0
test3.tabiya.local         : ok=0    changed=0    unreachable=1    failed=0
test4.tabiya.local         : ok=0    changed=0    unreachable=1    failed=0
test5.tabiya.local         : ok=0    changed=0    unreachable=1    failed=0
```