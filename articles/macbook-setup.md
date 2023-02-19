---
title: "MacBookをゼロからセットアップした"
emoji: "👨‍💻"
type: "idea" # tech: 技術記事 / idea: アイデア
topics: ["mac"]
published: false
---

Today I Learned というPodcastの第56回でMacのセットアップについて紹介されていて面白かったので、自分も書いてみることにした。

https://anchor.fm/todayilearnedfm/episodes/56--mac-e1kv1hc/a-a58emu

最近、新しいMacBookを購入した。サクサク動いてとても良い！

https://twitter.com/ryoishizawa/status/1626532483721465856?s=20

# システム設定（System Setting）

System Setting > Track Pad > Tap to Click

System Setting > General > Language & Region > Add japanese

System Setting > Keyboard > Text Input > Input Source > Edit > Turn off “Correct spelling automatically” and “Capitalise words automatically”

Dock - remove unnecessary icons (e.g. pages, numbers)

# Homebrew

最初に入れておくと、あとで色々インストールする際にコマンドでできることが多いので便利。

https://brew.sh/

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

自分の環境では上記のコマンドだけだと足りず、以下も実行してPATHに追加する必要があった。（これをしないと、`brew` コマンドが動かない）

```
(echo; echo 'eval "$(/opt/homebrew/bin/brew shellenv)"') >> /Users/username/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

# まず入れる

* 使っていれば、パスワード管理ツール (1Passwordなど)
* Chrome
* Zoom
* Slack
* Spotify
* Notion
* Inkdrop
* NordVPN
* Kindle
* VS Code
* IntelliJ

Homebrewを使えば、インストールが楽になる（途中で気付いた）。
例えば、Notionを入れたいなら以下のコマンド一発でインストールできる。

```
brew install --cask notion
```

# GitHub

GitHub > Settings > SSH and GPG keys

Commandでgitコマンドを打ったところ、Developer Toolのプロンプトが出たのでインストール

```
git config --global user.email "email"
git config --global user.name "name"
```

# Zenn

* nodejs

```
npm install
npx zenn new:article
```

# Zoom

Setting > Video > Stop my video when joining a meeting
Setting > Audio 
> Mute my mic when joining a meeting
> Automatically join computer audio when joining a meeting

# 便利ツール

## MonitorControl

https://github.com/MonitorControl/MonitorControl

外付けディスプレイの画面調整ができるのが最高すぎる。

## RunCat

https://kyome.io/runcat/index.html

PCのメモリやCPUの状態を把握するのに便利。M1以降だとPCのパフォーマンスが良いのでそんなに要らないかもしれないが、見た目的にも面白いので引き続き入れてる。

## Raycast

https://www.raycast.com/

もう定番になっている気がする。

設定：Spotlight Searchとしても利用したいので、System Setting > Keyboard shortcut > Spotlight > "Show Spotlight search" をオフにし、Command + Spaceをショートカットに設定している。

## CleanShot

https://cleanshot.com/

スクリーンショットやスクリーン上で動画を撮るときに便利で、編集を簡単にできてとても便利。仕事でもよく使ってて、もう手放せない。

## Video Speed Controller

https://chrome.google.com/webstore/detail/video-speed-controller/nffaoalbilbmmfgbnbgppjihopabppdk?hl=en

動画の速度を調整できるChrome Extention。YouTubeやUdemy等では標準で速度調整ができるので「本当に必要か？」と思ってたのだけど、このツイートの英語を聞き取りたくて入れた。入れてみると確かに便利だなと感じる。

https://twitter.com/DB_Daijiro/status/1627222586567589890

# OpenJDK, Scala

後々使いそうな気がするので入れておいた。

```
brew install openjdk@17
brew install openjdk@11
brew install scala
```

# Logi options

logitech.com/en-us/setup/ergosetup/logi-options.html
