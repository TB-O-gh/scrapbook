# gnome上でCtlとCapsLockを入れ替える。

``` bash
sudo vi /etc/default/keyboard
```

``` bash
XKBOPTIONS="ctrl:nocaps"
```

``` bash
sudo systemctl restart console-setup
```

再ログインする
