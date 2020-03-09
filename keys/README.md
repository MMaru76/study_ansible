# 一般ユーザー

```
mkdir .ssh/ ; \
chmod 700 .ssh/ ; \
touch .ssh/authorized_keys ; \
chmod 644 .ssh/authorized_keys ; \
vi .ssh/authorized_keys
```


# root ユーザー

```
mkdir .ssh/ ; \
chmod 700 .ssh/ ; \
cp /home/maru/.ssh/authorized_keys .ssh/authorized_keys
```