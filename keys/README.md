```
mkdir .ssh/
chmod 600 .ssh/
touch .ssh/authorized_keys
chmod 644 .ssh/authorized_keys
mv local_lan_key.pub .ssh/authorized_keys
```