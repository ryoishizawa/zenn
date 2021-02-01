---
title: "WSL2のターミナルで色が正常に表示されない時の解消方法"
emoji: "⛳"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["wsl"]
published: true
---

# 問題

WSL2(Ubuntu-20.04)のターミナルで色が正常に表示されない。

### 色が表示されている状態

![](https://storage.googleapis.com/zenn-user-upload/yc56cu83cqovcuwxp3hp8crjf3im)

### 色が表示されていない状態

![](https://storage.googleapis.com/zenn-user-upload/5pjty4j2bt1sxyz117p1b6bxhrwl)

# 原因

調べていくと、`source ~/.bashrc` を実行すると色が表示されることが分かり、ターミナル起動時に呼ばれるはずの `~/.bashrc` が読み込まれていないことが判明。

以下のIssue内のコメントにある通り、`~/.bash_profile` と `~/.profile` が両方存在している状態で、この場合は `~/.bash_profile` が読み込まれ、結果として `~/.profile` から呼ばれる `~/.bashrc` が正常に呼ばれていなかった。

https://github.com/microsoft/WSL/issues/2067#issuecomment-299622057

# 解消方法

最終的に、`~/.bash_profile` に以下のコードを追加することで解消できた。

```bash:.bash_profile
if [[ -f ~/.bashrc ]] ; then
  . ~/.bashrc
fi
```
