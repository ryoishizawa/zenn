---
title: "MacBookを買った時に行うセットアップ"
emoji: "👨‍💻"
type: "idea" # tech: 技術記事 / idea: アイデア
topics: ["mac"]
published: true
published_at: 2023-09-02 09:00 
---

Today I Learned というPodcastの第56回でMacのセットアップについて紹介されていて面白かったので、自分も書いてみることにした。

https://anchor.fm/todayilearnedfm/episodes/56--mac-e1kv1hc/a-a58emu

2月に新しいMacBookを買ってから記事を書いていたのだけど、下書きの状態で半年弱眠らせてしまった…。なので、今見ると設定の文言が変わったりしているかもしれない（OSはVenture）。

https://twitter.com/ryoishizawa/status/1626532483721465856?s=20

ちなみに自分はOSの設定とキーボードは英語にしているので、日本語を使った場合は不要な設定もいくつか混じっているが、ご容赦いただけると。

# システム設定（System Setting）

他にも使いつつ設定をいじっている気がしますが、まずは以下の設定。

* Track Pad > Tap to Click（トラックパットでタップしたときはクリックとして認識する）
* General > Language & Region > Add japanese（日本語を追加）
* Keyboard > Text Input > Input Source > Edit > Turn off “Correct spelling automatically” and “Capitalise words automatically”（入力の自動補正をオフ）

あとは、Dock上で普段使わないアイコン（Pages, Numbersなど）は削除する。

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

* パスワード管理ツール (1Passwordなど)
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

Zennの前に、まずnodejsを入れておく必要がある。

```
npm install
npx zenn new:article
```

# Zoom

インストールするのは当然として、初期設定のまま使っている人を結構見かける。個人的にはいくつかデフォルトから変えておくべきだと思っている。

* Setting > Video > Stop my video when joining a meeting
* Setting > Audio 
  * Mute my mic when joining a meeting（ミーティングに参加したときにマイクをミュートにする）
  * Automatically join computer audio when joining a meeting（ミーティングに参加したときに自動で音が入るようにする）

# zsh

## oh-my-zsh

Terminal用にはoh-my-zshを使っている。Terminal内でGitのどのブランチにいるのか等がぱっと見えるのが便利なのと、あとは単純に見た目が良くなる。

https://ohmyz.sh/#install

自分で好きなテーマを設定できるので、ここから探してみると良いかと思う。

https://github.com/ohmyzsh/ohmyzsh/wiki/Themes

## zsh-autosuggestions

https://github.com/zsh-users/zsh-autosuggestions

コマンドをサジェストしてくれるプラグイン。

## zsh-syntax-highlighting

https://github.com/zsh-users/zsh-syntax-highlighting

こちらはコマンドをハイライトしてくれるプラグイン。

# OpenJDK, Scala

私はバックエンドエンジニアでJavaやScalaを書いているので、とりあえずインストール。

```
brew install openjdk@17
brew install openjdk@11
brew install coursier/formulas/coursier && cs setup
```

# 便利ツール

## MonitorControl

https://github.com/MonitorControl/MonitorControl

外付けディスプレイの画面調整ができるのが最高すぎる。

## RunCat

https://kyome.io/runcat/index.html

PCのメモリやCPUの状態を把握するのに便利。M1以降だとPCのパフォーマンスが良いのでそんなに要らないかもしれないが、見た目的にも面白いので引き続き入れてる。

## Raycast

https://www.raycast.com/

もう定番になっている（？）便利ツール。

設定：Spotlight Searchとしても利用したいので、System Setting > Keyboard shortcut > Spotlight > "Show Spotlight search" をオフにし、Command + Spaceをショートカットに設定している。

## CleanShot

https://cleanshot.com/

スクリーンショットやスクリーン上で動画を撮るときに便利で、編集を簡単にできてとても便利。仕事でもよく使ってて、もう手放せない。

## Video Speed Controller

https://chrome.google.com/webstore/detail/video-speed-controller/nffaoalbilbmmfgbnbgppjihopabppdk?hl=en

動画の速度を調整できるChrome Extention。YouTubeやUdemy等では標準で速度調整ができるので「本当に必要か？」と思ってたのだけど、このツイートの英語を聞き取りたくて入れた。入れてみると確かに便利だなと感じる。

https://twitter.com/DB_Daijiro/status/1627222586567589890

## DeepL

おなじみの翻訳ツール。

Chrome Extentionもある。Proになるとページを全て翻訳することもできるらしい。

https://chrome.google.com/webstore/detail/deepl-translate-reading-w/cofdbpoegempjloogbagkncekinflcnj/related

## Logi options

自分が使っているLogicoolのマウス用のアプリ。

https://logitech.com/en-us/setup/ergosetup/logi-options.html

## Karabiner-Elements

https://karabiner-elements.pqrs.org/

キーマップを変更できる便利アプリ。

他にも色々入れているものがある気がするが、一旦ここまで。次またセットアップする機会があればまた書きたい。
