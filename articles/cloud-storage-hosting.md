---
title: "Cloud Storageに静的ページをホストする"
emoji: "🌐"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["googlecloud"]
published: false
---

Google Cloud公式で詳しく丁寧に書かれているので記事にするほどでも無いが、ドメインを取得してCloud Storageでページをホストする方法を簡単にメモ。

# ドメイン取得

ドメイン取得で今回はGandiを利用してみた。

https://www.gandi.net/

Gandiについてはこちらの記事に詳しく書かれているので参考にすると良いと思う。[rebuild.fm](https://rebuild.fm/)で紹介されていたのを聴いて、自分でも使ってみることにしてみた。正直のところ自分でドメインを取得するのは初めてなので他のサービスとは比較できないが、今のところ特に問題なく利用できている。

https://zenn.dev/northeggman/articles/9194968d5d084c

# Google Cloudでホスティング

今回はJavaScriptすら無い静的ページを簡単にホストしたかったので、Google CloudのCloud Storageを使えば簡単だろうなと思って使ってみることにした。自分でhtmlを用意した後、以下の公式ページの手順を進めていけば確実にページを作成できる。

https://cloud.google.com/storage/docs/hosting-static-website

ドキュメントに沿って、以下の手順を踏む。

* Cloud Storageのバケット作成
* ファイルのアップロード
* SSL証明書作成
* ロードバランサーの設定

# Gandiでドメイン設定

ドメイン設定で注意が必要だったのは、wwwの設定だった。

自分のドメインが「example.com」だったとして、「www.example.com」をどう名前解決するかという設定だが、Google CloudのドキュメントではAレコードで設定するように記載されている。

しかし、Gandi上ではwwwについてはCNAMEで初期設定が入っているので、いずれかの方法を取る必要がある。

* wwwのCNAMEレコードを変更し、自分のドメイン（上記の例だとexample.com）に接続するようにする
* wwwのCNAMEレコードを削除し、Aレコードでwwwの設定を自分のIPアドレスに接続するようにする

自分の場合は1つ目の手法を選択し、無事wwwが付いたURLでも接続できるようになった。

# 追記

Cloud Storageでバケットにファイルをアップロードしてインターネットに公開した際、バケットのURLを入れるとXMLでファイル一覧が表示されるのが気にかかっていた。

![](/images/cloud-storage-xml.png)

このXMLでのファイル一覧を表示しないようにするには、バケット詳細ページ > 権限 から権限の変更をする。

「allUsers」の設定箇所で編集ボタン（鉛筆のアイコン）をクリックする。

![](/images/cloud-storage-setting-1.png)

権限を、Cloud Storage レガシー > Storage レガシー オブジェクト読み取り に変更する。

![](/images/cloud-storage-setting-2.png)

この設定をすることで、XMLでの表示が「Access Denied」になる。

![](/images/cloud-storage-xml-403.png)

この設定は、こちらの記事を参考にさせて頂きました。（記事は2021年のものですが、2023年でも同じく設定できました）

https://zenn.dev/catnose99/articles/18720e3af36d22