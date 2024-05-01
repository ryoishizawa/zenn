---
title: "Java GCアルゴリズムの種類"
emoji: "🐷"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["java"]
published: false
---
 
# Serial GC ‐ シリアル型ガベージコレクター

1つのスレッドのみで処理を行うガベージコレクター。スレッドを1つしか使わないのでCPUの消費量は少ないが、フルGCの際はアプリケーションの処理を完全に停止した上で処理することになってしまう。
CPUの割当が少ないVMやコンテナ上で選択肢となり得る。

有効にする場合には `-XX:+UseSerialGC` を指定する。`-` を使って無効にすることはできないので、このGCがデフォルトになっている環境で別のアルゴリズムを使いたい場合は、別のアルゴリズムを明示的に指定する必要がある。

# Throughput (Parallel) GC ‐ スループット型ガベージコレクター



# G1 GC

# Concurrent Mark-Sweep (CMS)

# ZGC

# Shenandoah

# Epsilon GC
