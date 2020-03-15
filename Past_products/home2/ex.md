# サーバーで実行したコマンドの備忘録

## 秘密鍵の送信方法

```
ssh-copy-id -o StrictHostKeyChecking=no -i ~/.ssh/id_rsa.pub ans181.tabiya.local
```

## 作業ディレクトリを作成
```
mkdir -vp PATH_TO/effective_ansible/sec2/inventory
```

## 対象のホストに対してpingの送信

```
ansible -i inventory/test01_inventory.ini test_ans_servers -m ping
```

## 対象のホストに対してファイルのリモート作成
```
ansible -i inventory/test01_inventory.ini test_ans_servers -m file -a 'path=/home/maru/test1.txt state=touch mode=0644'
```