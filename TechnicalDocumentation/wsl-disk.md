# wsl ディスク削減

## wslをシャットダウン

``` bash
wsl --shutdown
```

## ディスクパート起動

``` bash
diskpart
```

## 容量削減

``` bash
DISKPART> select vdisk file="D:\wsl2\ubuntu\ext4.vhdx"
DISKPART> compact vdisk
DISKPART> exit
```
