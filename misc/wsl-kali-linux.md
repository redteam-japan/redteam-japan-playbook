
## WSLのインストール

### コマンドプロンプトを管理者権限で実行
<figure><img src="../assets/Pasted image 20250310210053.png" alt=""><figcaption></figcaption></figure>


![[Pasted image 20250318210839.png]]

### WSLの有効化

#### コマンド
```cmd {iscopy=true}
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

#### コマンド実行結果（再起動が必要）
```cmd
C:\Windows\System32>dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart

展開イメージのサービスと管理ツール
バージョン: 10.0.26100.1150

イメージのバージョン: 10.0.26100.3476

機能を有効にしています
[==========================100.0%==========================]
操作は正常に完了しました。


C:\Windows\System32>dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all

展開イメージのサービスと管理ツール
バージョン: 10.0.26100.1150

イメージのバージョン: 10.0.26100.3476

機能を有効にしています
[==========================100.0%==========================]
操作は正常に完了しました。
Windows を再起動してこの操作を完了してください。
今すぐコンピューターを再起動しますか? (Y/N)
```

### WSLを最新バージョンにアップデート

#### コマンド
```cmd {iscopy=true}
wsl --update
```

#### コマンド実行例
```cmd
C:\Windows\System32>wsl --update
ダウンロード中: Linux 用 Windows サブシステム 2.4.12
インストール中: Linux 用 Windows サブシステム 2.4.12
Linux 用 Windows サブシステム 2.4.12 はインストールされました。
この操作を正しく終了しました。
更新プログラムを確認しています。
Linux 用 Windows サブシステムの最新バージョンは既にインストールされています。
```

### WSL のバージョンを WSL2 に設定

#### コマンド
```cmd {iscopy=true}
wsl --set-default-version 2
```

#### コマンド実行例

```cmd
C:\Windows\System32>wsl --set-default-version 2
WSL 2 との主な違いについては、https://aka.ms/wsl2
 を参照してください
この操作を正しく終了しました。
```

## Kali Linuxのインストール

### Kali Linux をインストール
WSL に Kali Linux をインストールします。
#### コマンド
```cmd {iscopy=true}
wsl --install -d kali-linux
```

#### コマンド実行例
```cmd
C:\Windows\System32>wsl --install -d kali-linux
ダウンロード中: Kali Linux Rolling
インストール中: Kali Linux Rolling
ディストリビューションが正常にインストールされました。'wsl.exe -d kali-linux' を使用して起動できます
```

### Kali Linuxの初期設定
WSL の Kali を起動し、初期設定を行います。
#### コマンド
```cmd {iscopy=true}
wsl -d kali-linux
```

#### コマンド実行例
この例はユーザー名を`kali`にしています。
```cmd
C:\Windows\System32>wsl -d kali-linux
Waiting for systemd to start...
running
Please create a default Kali WSL user. The username does not need to match your Windows username.
For more information visit: https://aka.ms/wslusers
Enter new UNIX username: kali
New password:
Retype new password:
passwd: password updated successfully
┏━(Message from Kali developers)
┃
┃ This is a minimal installation of Kali Linux, you likely
┃ want to install supplementary tools. Learn how:
┃ ⇒ https://www.kali.org/docs/troubleshooting/common-minimum-setup/
┃
┗━(Run: “touch ~/.hushlogin” to hide this message)
┌──(kali㉿youtube)-[/mnt/c/Windows/System32]
└─$
```

### WSL用のGUIをインストール
WSL2 では GUI を利用できるようになっているので、デスクトップ環境（Xfce）をインストールします。

```bash {iscopy=true}
sudo apt update && sudo apt upgrade -y
sudo apt install -y kali-linux-large
```

#### Configuring macchanger

<figure><img src="../assets/Pasted image 20250318213544.png" alt=""><figcaption></figcaption></figure>
#### Configuring kismet-capture-common①
ワイヤレス向けのペンテストツール「Kismet」の設定を行います。  
Kismetを`sudo`で動作させると問題が発生することがあるため、`kismet`グループを作成する必要があります。  
そのため、セットアップ時に **「Yes」** を選択しました。


<figure><img src="../assets/Pasted image 20250318213618.png" alt=""><figcaption></figcaption></figure>
#### Configuring kismet-capture-common②
  
次に、「Users to add to the kismet group」には自分のユーザー名を入力します。
<figure><img src="../assets/Pasted image 20250318213654.png" alt=""><figcaption></figcaption></figure>


#### Configuring wireshark-common
パケット解析ツール「Wireshark」を`sudo`なしで使用できるようにするかどうかの設定です。  
**「Yes」** を選択しました。
<figure><img src="../assets/Pasted image 20250318213720.png" alt=""><figcaption></figcaption></figure>

#### sslh configuration
`sslh` の設定時に、動作モードとして **「standalone」** を選択します。  
「standalone」モードでは、`sslh` が単独のサービスとして動作し、直接ポートをリッスンします。  
システムの`inetd`や他のスーパーデーモンに依存せずに動作するため、一般的な用途では **「standalone」** を選択するのが推奨されます。

<figure><img src="../assets/Pasted image 20250318213811.png" alt=""><figcaption></figcaption></figure>

### Kali LinuxのGUI起動

#### `startxfce4`コマンドを実行します。
```bash {iscopy=true}
startxfce4
```

#### 実行後、Kali Linuxのタスクバーが表示されます。
<figure><img src="../assets/Pasted image 20250318220345.png" alt=""><figcaption></figcaption></figure>

#### WindowsのタスクバーにLinuxアイコンが2つ表示されます。

- 1つはKali Linuxのタスクバー
- もう1つはKali Linuxのデスクトップ  
    Kali Linuxのデスクトップを開くには、デスクトップのアイコンをクリックします。
<figure><img src="../assets/Pasted image 20250318220417.png" alt=""><figcaption></figcaption></figure>

#### Kali Linuxのデスクトップが表示され、GUI環境が利用できるようになります。
<figure><img src="../assets/Pasted image 20250318220443.png" alt=""><figcaption></figcaption></figure>


#### 終了するには、`startxfce4` を実行したターミナルで `Ctrl + X` を押します。
<figure><img src="../assets/Pasted image 20250318220644.png" alt=""><figcaption></figcaption></figure>

### Kali LinuxのアプリをWindowsから起動する

#### **方法①：スタートメニューから起動**

1. Windowsの **スタートメニュー** を開く
2. 「Kali Linux」または「Kali」 と検索
3. 表示された「Kali Linux」アプリをクリック（例: `firefox` を起動）
<figure><img src="../assets/Pasted image 20250318222308.png" alt=""><figcaption></figcaption></figure>

4. KaliのFirefoxが起動する
 <figure><img src="../assets/Pasted image 20250318222347.png" alt=""><figcaption></figcaption></figure>



#### **方法②：特定のGUIアプリを直接起動**

Kali LinuxのGUIアプリ（例: `xfce4-terminal` や `firefox`）を直接起動することも可能です。

1. **PowerShell** または **コマンドプロンプト（cmd）** を開く
2. 以下のコマンドを実行（例: `firefox` を起動）
```cmd
wsl -d kali-linux -- firefox
```
3. Kali LinuxのFirefoxがGUIで起動する
<figure><img src="../assets/Pasted image 20250318222758.png" alt=""><figcaption></figcaption></figure>

他のGUIアプリも同様に、以下のように実行できます。

| アプリ                    | コマンド                           |
| ---------------------- | ------------------------------ |
| **ファイルマネージャー（Thunar）** | `wsl -d kali-linux -- thunar`  |
| **Firefox（ブラウザ）**      | `wsl -d kali-linux -- firefox` |
| **Gedit（テキストエディタ）**    | `wsl -d kali-linux -- gedit`   |