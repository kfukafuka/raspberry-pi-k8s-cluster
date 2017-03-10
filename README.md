# RaspberryPiでKubernetesのClusterを構築する
## OS準備
### Requirements
* wget
* pv
* awscli

### flashコマンドの準備
```bash
$ wget https://raw.githubusercontent.com/hypriot/flash/master/$(uname -s)/flash
$ chmod +x flash
$ sudo mv flash /usr/local/bin/flash
```
### flashコマンドの実行
* ssid/password は自分の環境に合わせて設定を行う
* hostnameはお好きなものをどうぞ
* imgはhttps://blog.hypriot.com/downloads/ から選択
* Is /dev/disk1 correct? は yes
* 途中でパスワードを聞かれます
* 「🍺  Finished.」 がでればOK
 
```bash
$ flash --ssid "access-point" --password "password" --hostname hostname https://github.com/hypriot/image-builder-rpi/releases/download/v1.1.3/hypriotos-rpi-v1.1.3.img.zip
```

### ログイン
* 初期はpirate/hypriotでログイン
* ssh -o PreferredAuthentications=password でパスワード認証にする
* ログイン時のhost名は設定したホスト名に.localがつく
```bash
$ ssh pirate@hostname.local -o PreferredAuthentications=password
pirate@hostname.local's password:

HypriotOS (Debian GNU/Linux 8)

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
HypriotOS/armv7: pirate@hostname in ~
```

# 参考URL
* https://github.com/hypriot/flash
* https://blog.hypriot.com/getting-started-with-docker-and-mac-on-the-raspberry-pi/
* http://blog.kubernetes.io/2015/11/creating-a-Raspberry-Pi-cluster-running-Kubernetes-the-shopping-list-Part-1.html
* http://blog.kubernetes.io/2015/12/creating-raspberry-pi-cluster-running.html
