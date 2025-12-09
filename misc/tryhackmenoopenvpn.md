# TryHackMeのOpenVPN接続

TryHackMeが提供するAttackBoxには、**無料アカウントの場合、1日1時間の利用制限**があります。そのため、Kali Linux環境を自分で構築し、OpenVPNを使用してTryHackMeのネットワークに接続することで、時間の制約なく演習を進めることができます。

### OpenVPNの設定ファイルのダウンロード

#### TryHackMeサイトに接続して、`プロフィールアイコン`をクリックします。

<figure><img src="../.gitbook/assets/Pasted image 20250312204640.png" alt=""><figcaption></figcaption></figure>

#### `Access`をクリックします。

<figure><img src="../.gitbook/assets/Pasted image 20250312204716.png" alt=""><figcaption></figcaption></figure>

#### `Download configuration file`をクリックし、OpenVPN設定ファイル（`.ovpn`）をダウンロードします。

<figure><img src="../.gitbook/assets/Pasted image 20250312204819.png" alt=""><figcaption></figcaption></figure>

#### ファイルを保存します。ファイルはKali Linux環境に移動する必要があります。

<figure><img src="../.gitbook/assets/Pasted image 20250312205009.png" alt=""><figcaption></figcaption></figure>

### OpenVPN接続

#### Kali Linux上のOpenVPNの設定ファイルを確認します。

```bash
ls
redteam.japan.ovpn
```

#### `sudo openvpn {.ovpnファイル}`を実行します。

```shell
sudo openvpn redteam.japan.ovpn
[sudo] password for kali:
2025-03-12 07:52:22 WARNING: Compression for receiving enabled. Compression has been used in the past to break encryption. Sent packets are not compressed unless "allow-compression yes" is also set.
2025-03-12 07:52:22 Note: --cipher is not set. OpenVPN versions before 2.5 defaulted to BF-CBC as fallback when cipher negotiation failed in this case. If you need this fallback please add '--data-ciphers-fallback BF-CBC' to your configuration and/or add BF-CBC to --data-ciphers.
2025-03-12 07:52:22 Note: '--allow-compression' is not set to 'no', disabling data channel offload.
2025-03-12 07:52:22 OpenVPN 2.6.12 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [LZ4] [EPOLL] [PKCS11] [MH/PKTINFO] [AEAD] [DCO]
2025-03-12 07:52:22 library versions: OpenSSL 3.4.0 22 Oct 2024, LZO 2.10
2025-03-12 07:52:22 DCO version: N/A
2025-03-12 07:52:22 TCP/UDP: Preserving recently used remote address: [AF_INET]18.202.129.195:1194
2025-03-12 07:52:22 Socket Buffers: R=[212992->212992] S=[212992->212992]
2025-03-12 07:52:22 UDPv4 link local: (not bound)
2025-03-12 07:52:22 UDPv4 link remote: [AF_INET]18.202.129.195:1194
2025-03-12 07:52:22 TLS: Initial packet from [AF_INET]18.202.129.195:1194, sid=3e27b0b7 982bf67b
2025-03-12 07:52:22 VERIFY OK: depth=1, CN=ChangeMe
2025-03-12 07:52:22 VERIFY KU OK
2025-03-12 07:52:22 Validating certificate extended key usage
2025-03-12 07:52:22 ++ Certificate has EKU (str) TLS Web Server Authentication, expects TLS Web Server Authentication
2025-03-12 07:52:22 VERIFY EKU OK
2025-03-12 07:52:22 VERIFY OK: depth=0, CN=server
2025-03-12 07:52:22 Control Channel: TLSv1.3, cipher TLSv1.3 TLS_AES_256_GCM_SHA384, peer certificate: 2048 bits RSA, signature: RSA-SHA256, peer temporary key: 253 bits X25519
2025-03-12 07:52:22 [server] Peer Connection Initiated with [AF_INET]18.202.129.195:1194
2025-03-12 07:52:22 TLS: move_session: dest=TM_ACTIVE src=TM_INITIAL reinit_src=1
2025-03-12 07:52:22 TLS: tls_multi_process: initial untrusted session promoted to trusted
2025-03-12 07:52:23 SENT CONTROL [server]: 'PUSH_REQUEST' (status=1)
2025-03-12 07:52:23 PUSH: Received control message: 'PUSH_REPLY,route 10.10.0.0 255.255.0.0,route 10.101.0.0 255.255.0.0,route 10.103.0.0 255.255.0.0,route-metric 1000,comp-lzo no,route-gateway 10.8.0.1,topology subnet,ping 5,ping-restart 120,ifconfig 10.8.74.166 255.255.0.0,peer-id 227,cipher AES-256-CBC'
2025-03-12 07:52:23 OPTIONS IMPORT: --ifconfig/up options modified
2025-03-12 07:52:23 OPTIONS IMPORT: route options modified
2025-03-12 07:52:23 OPTIONS IMPORT: route-related options modified
2025-03-12 07:52:23 net_route_v4_best_gw query: dst 0.0.0.0
2025-03-12 07:52:23 net_route_v4_best_gw result: via 192.168.93.2 dev eth0
2025-03-12 07:52:23 ROUTE_GATEWAY 192.168.93.2/255.255.255.0 IFACE=eth0 HWADDR=00:0c:29:96:9b:0c
2025-03-12 07:52:23 TUN/TAP device tun0 opened
2025-03-12 07:52:23 net_iface_mtu_set: mtu 1500 for tun0
2025-03-12 07:52:23 net_iface_up: set tun0 up
2025-03-12 07:52:23 net_addr_v4_add: 10.8.74.166/16 dev tun0
2025-03-12 07:52:23 net_route_v4_add: 10.10.0.0/16 via 10.8.0.1 dev [NULL] table 0 metric 1000
2025-03-12 07:52:23 net_route_v4_add: 10.101.0.0/16 via 10.8.0.1 dev [NULL] table 0 metric 1000
2025-03-12 07:52:23 net_route_v4_add: 10.103.0.0/16 via 10.8.0.1 dev [NULL] table 0 metric 1000
2025-03-12 07:52:23 Initialization Sequence Completed
2025-03-12 07:52:23 Data Channel: cipher 'AES-256-CBC', auth 'SHA512', peer-id: 227, compression: 'stub'
2025-03-12 07:52:23 Timers: ping 5, ping-restart 120

```

#### 別のターミナルでIPアドレスを確認します。`ip a`コマンドを実行して、`tun0`インターフェースのIPアドレスを確認します。

```shell
$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:0c:29:96:9b:0c brd ff:ff:ff:ff:ff:ff
    inet 192.168.93.5/24 brd 192.168.93.255 scope global noprefixroute eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::5be3:d534:d90b:5c9d/64 scope link noprefixroute
       valid_lft forever preferred_lft forever
3: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 500
    link/none
    inet 10.8.74.166/16 scope global tun0
       valid_lft forever preferred_lft forever
    inet6 fe80::db4c:b1c3:cd43:efd/64 scope link stable-privacy proto kernel_ll
       valid_lft forever preferred_lft forever

```
