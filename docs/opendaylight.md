## ODLの使い方

### 起動方法

```sh
# opendaylightのディレクトリにて
./bin/karaf       # 通常起動
./bin/karaf clean # 初期化して起動
```

### feature関係

OpenDaylightではfeatureを追加することで様々な機能を追加することができます。
ちなみにfeatureを追加していない初期状態はほとんど何もできない状態です。

```sh
feature:list                   # featureのリストを表示
feature:list -i                # installされているfeatureのリストを表示
feature:install <FEATURE_NAME> # featureのインストール
```
#### 便利なfeature

|feature名|機能|
|:---:|:---|
|odl-dlux-core|ブラウザからトポロジーを見れたりする便利なdlux|
|odl-restconf|northbound apiからフローを書き換えたりするためのfeature|
|odl-l2switch-switch|スイッチをl2switchと同じように動作させるためのfeature|

### ログ関係

ODLではログを```./data/log/karaf.log```に保存している。
もしログを見てデバッグなどする必要があればここを参照する。
