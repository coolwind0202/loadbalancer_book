---
title: "DNSラウンドロビン"
---


## ドメイン名とは
ネットワーク上のコンピュータにアクセスするためには、そのコンピュータがもつIPアドレスを指定する必要があります。
しかし、IPアドレス（IPv4アドレス）は4つの数値で構成されており、人間にとって覚えにくく、扱いにくいものでした。
![IPアドレスのみのとき](/images/dns_roundrobin/ip_address.png)

そこで、IPアドレスに **ドメイン名** という名前を付けて管理する考え方が生まれました。
![ドメイン名で管理する](/images/dns_roundrobin/domain_name.png)
## DNSを利用した名前解決
ネットワーク上のコンピュータにアクセスする場合、ドメイン名に対応するIPアドレスを割り出す必要があります。
ドメイン名をIPアドレスに変換することを **名前解決** といいます。

現在のインターネットにおいては、DNS（Domain Name System）を利用した名前解決が一般的です。

DNSを利用した名前解決では、名前解決機能を提供する「DNSサーバー」にリクエストを行います。
DNSサーバーは、リクエスト元のDNSクライアントに対し、ドメイン名に対応するIPアドレスなどの情報をレスポンスとして返します。

（図）

## 演習: DNSを利用した名前解決
### digコマンドの使用方法
演習環境: `dns_roundrobin`

`dig`コマンドで、DNSサーバーへリクエストを送り、そのレスポンスを取得します。
次の例では、ドメイン名 `example.home` に対応するIPアドレスを取得しています。

```sh
dig example.home
```

次のようなレスポンスがDNSサーバーから返却されます。

```

```

レスポンスには、「レコード」という単位でデータが格納されます。
ドメイン名に対応するIPアドレスを表すのは、Answerに含まれる **「A」のレコード** です。
したがって、ドメイン名`example.home`に対応するIPアドレスは `192.168.0.1` と分かります。

#### 問1
ドメイン名 `q1.home` に対応するIPアドレスを取得してください。

:::details 解答例
`dig`コマンドを次のように実行します。
```sh
dig q1.home
```

レスポンスは次のようになります。

```

```

レスポンスに含まれるAレコードを確認することで、`q1.home`に対応するIPアドレスは `10.0.0.1` と分かります。
:::

#### 問2
ドメイン名 `q2.home`に対応するIPアドレスを取得してください。

:::details 解答例
`dig`コマンドを次のように実行します。
```sh
dig q1.home
```

レスポンスは次のようになります。

```

```

このように、DNSサーバーが複数のAレコードを返すこともあります。
**一つのドメイン名に複数のIPアドレス**が関連づいており、**どのIPアドレスに接続するかは自由**です。
:::

### ネームサーバーの指定

## フルサービスリゾルバの動き

## 演習: フルサービスリゾルバの動き
フルサービスリゾルバの「再帰的問い合わせ」の方法を真似ながら、ドメイン名 `www.chitose.ac.jp` に対応するIPアドレスを取得します。

### ルートサーバーに問い合わせ

最初に調べる必要があるのは、`.jp`の情報をもつ権威サーバーです。

### `.jp`の権威サーバーに問い合わせ

### `.chitose.ac.jp`の権威サーバーに問い合わせ


