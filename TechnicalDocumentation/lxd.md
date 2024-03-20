# lxd install

Ubuntu22.04で実行
```bash
sudo snap install lxd
```

基本的にデフォルトのままで答えていく。  
```bash
sudo lxd init  
```

ipv4許可
```bash
sudo ufw allow in on lxdbr0
sudo ufw route allow in on lxdbr0
sudo ufw reload
```

kali-currentコンテナを構築  
```bash
sudo lxc launch images:kali kali-current
```

## kali install

kaliセットアップ
``` bash
lxc launch images:kali/current/amd64 my-kali  
```

アップデート、パッケージ導入
``` bash
lxc exec my-kali -- apt update  
lxc exec my-kali -- apt install -y kali-linux-default 
```
ユーザーセットアップと設定
``` bash
lxc exec my-kali -- adduser kali
lxc exec my-kali -- usermod -aG sudo kali
lxc exec my-kali -- sed -i '1 i\TERM=xterm-256color' /home/kali/.bashrc
lxc exec my-kali -- sh -c "echo 'Set disable_coredump false' > /etc/sudo.conf"
```

コンソール接続
``` bash
lxc console my-kali
```

コンソールからのデタッチ
``` bash
CTRL+a q
```
