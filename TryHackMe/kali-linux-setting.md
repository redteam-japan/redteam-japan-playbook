## Kali Linuxのダウンロード

本資料では、Windows 11環境でTryHackMe用のKali Linux仮想マシンをVMware上に構築する手順を説明します。初心者の方でも迷わずセットアップできるよう、画像とともに詳しく解説します。


### [ダウンロードリンク](https://www.kali.org/get-kali/#kali-platforms)サイトにアクセスします。

### `Virtual Machines`をクリックします。

<figure><img src="../assets/Pasted image 20250310210053.png" alt=""><figcaption></figcaption></figure>

### `VMware`の`↓`クリックして、ファイルを保存します。
<figure><img src="../assets/Pasted image 20250310210201.png" alt=""><figcaption></figcaption></figure>


## Kali Linuxの仮想マシン追加
`Kali Linux`をダウンロードすると、拡張子が `.7z` のファイル形式 になっています。
この`.7z`ファイルを展開するには、専用の解凍ソフトが必要 です。

本手順では、`Bandizip` を使用した環境を前提としています。
`7zip`、`Bandizip`などの解凍ソフトがインストールされていない場合は、事前にインストールしてください。

### ダウンロードしたファイルを展開します。
<figure><img src="../assets/Pasted image 20250310212111.png" alt=""><figcaption></figcaption></figure>

### 展開先を指定して、`展開`をクリックします。
<figure><img src="../assets/Pasted image 20250310212201.png" alt=""><figcaption></figcaption></figure>

### 解凍が完了するまで、少々お待ちください。
<figure><img src="../assets/Pasted image 20250310212224.png" alt=""><figcaption></figcaption></figure>

### （選択事項）完了したら、フォルダ名を変更します。
<figure><img src="../assets/Pasted image 20250310212528.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../assets/Pasted image 20250310212557.png" alt=""><figcaption></figcaption></figure>

### `VMware Workstation`を起動して、`仮想マシンを開く`をクリックします。
<figure><img src="../assets/Pasted image 20250310212637.png" alt=""><figcaption></figcaption></figure>

### 解凍したフォルダに移動して、`vmx`拡張子のファイルを選択し、`開く`をクリックします。
<figure><img src="../assets/Pasted image 20250310212929.png" alt=""><figcaption></figcaption></figure>

### 仮想マシンの名前およびハードウェア設定を変更します。
<figure><img src="../assets/Pasted image 20250310213017.png" alt=""><figcaption></figcaption></figure>

### 仮想マシンを右クリックし、`設定'をクリックします。
<figure><img src="../assets/Pasted image 20250310213137.png" alt=""><figcaption></figcaption></figure>

### メモリを`8GB`をクリックします。
<figure><img src="../assets/Pasted image 20250310213239.png" alt=""><figcaption></figcaption></figure>

### `オプション`タブをクリックします。
<figure><img src="../assets/Pasted image 20250310213318.png" alt=""><figcaption></figcaption></figure>


### 仮想マシン名を変更します。
<figure><img src="../assets/Pasted image 20250310213414.png" alt=""><figcaption></figcaption></figure>


### `OK`をクリックします。
<figure><img src="../assets/Pasted image 20250310213453.png" alt=""><figcaption></figcaption></figure>

### 仮想マシン名およびメモリ設定が変更されていることを確認します。
<figure><img src="../assets/Pasted image 20250310213529.png" alt=""><figcaption></figcaption></figure>


## Kali Linuxの設定

### `▶`ボタンをクリックして、マシンをパワーオンします。
<figure><img src="../assets/Pasted image 20250310213646.png" alt=""><figcaption></figcaption></figure>


### 起動が完了するまでに少々お待ちください。
<figure><img src="../assets/Pasted image 20250310213717.png" alt=""><figcaption></figcaption></figure>


### ログイン画面が表示されたら起動完了です。ユーザー`kali` パスワード`kali`を入力してログインします。
<figure><img src="../assets/Pasted image 20250310213754.png]" alt=""><figcaption></figcaption></figure>

### デスクトップを右クリックします。
<figure><img src="../assets/Pasted image 20250310213838.png" alt=""><figcaption></figcaption></figure>


### `Open Terminal Here`をクリックします。
<figure><img src="../assets/Pasted image 20250310214008.png" alt=""><figcaption></figcaption></figure>

### ターミナルが開きました。
<figure><img src="../assets/Pasted image 20250310214040.png" alt=""><figcaption></figcaption></figure>



### `sudo apt update`で最新のリポジトリ情報を取得します。
```shell
┌──(kali㉿kali)-[~/Desktop]
└─$ sudo apt update
[sudo] password for kali: 
Get:1 http://ftp.yz.yamagata-u.ac.jp/pub/linux/kali kali-rolling InRelease [41.5 kB]
Get:2 http://ftp.yz.yamagata-u.ac.jp/pub/linux/kali kali-rolling/main amd64 Packages [20.6 MB]
Get:3 http://ftp.yz.yamagata-u.ac.jp/pub/linux/kali kali-rolling/main amd64 Contents (deb) [49.1 MB]
Get:4 http://ftp.yz.yamagata-u.ac.jp/pub/linux/kali kali-rolling/contrib amd64 Packages [115 kB]
Get:5 http://ftp.yz.yamagata-u.ac.jp/pub/linux/kali kali-rolling/contrib amd64 Contents (deb) [267 kB]
Get:6 http://ftp.yz.yamagata-u.ac.jp/pub/linux/kali kali-rolling/non-free amd64 Packages [202 kB]
Get:7 http://ftp.yz.yamagata-u.ac.jp/pub/linux/kali kali-rolling/non-free amd64 Contents (deb) [884 kB]
Get:8 http://ftp.yz.yamagata-u.ac.jp/pub/linux/kali kali-rolling/non-free-firmware amd64 Packages [10.8 kB]
Get:9 http://ftp.yz.yamagata-u.ac.jp/pub/linux/kali kali-rolling/non-free-firmware amd64 Contents (deb) [24.3 kB]
Fetched 71.3 MB in 13s (5,385 kB/s)                                         
1504 packages can be upgraded. Run 'apt list --upgradable' to see them.
                                                                          
```

### `ssh`を有効にします。
`ssh`を有効にするのは選択事項です。
```shell
┌──(kali㉿kali)-[~/Desktop]
└─$ sudo systemctl enable ssh
Synchronizing state of ssh.service with SysV service script with /usr/lib/systemd/systemd-sysv-install.
Executing: /usr/lib/systemd/systemd-sysv-install enable ssh
Created symlink '/etc/systemd/system/sshd.service' → '/usr/lib/systemd/system/ssh.service'.
Created symlink '/etc/systemd/system/multi-user.target.wants/ssh.service' → '/usr/lib/systemd/system/ssh.service'.
                                                                             
┌──(kali㉿kali)-[~/Desktop]
└─$ sudo systemctl start ssh 

┌──(kali㉿kali)-[~/Desktop]
└─$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:0c:29:f3:91:ea brd ff:ff:ff:ff:ff:ff
    inet 192.168.202.128/24 brd 192.168.202.255 scope global dynamic noprefixroute eth0
       valid_lft 1295sec preferred_lft 1295sec
    inet6 fe80::1c39:f729:1c66:918e/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

```


### sshで接続できました。
<figure><img src="../assets/Pasted image 20250310214726.png" alt=""><figcaption></figcaption></figure>


