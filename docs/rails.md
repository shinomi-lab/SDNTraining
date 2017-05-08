## rails開発

### railsとは

ruby on railsはWebアプリケーションフレームワークです。

フレームワークを用いることで生産性が向上したり、同じようなコードを書くことでメンテナンス性が高くなります。

railsは以下の3つの特徴?思想?があります
- Model View Controller
- Don't Repeat Yourself(同じ記述を繰り返さない)
- Convention over Configuration(設定より規約)

詳細については調べてください。

### 基本的なファイル構成

railsでアプリを作成すると以下のようなディレクトリ構造でファイルが作成されます。

railsではディレクトリ構造が決まっているので、自分でファイルを探すときに簡単に見つけることができます。(ちゃんと正しい場所にファイルを置いていれば)

```
/app
  /assets
    /images       - 画像ファイル
    /JavaScripts  - javascriptファイル
    /stylesheets  - cssファイル
  /controllers    - コントローラー
  /helpers        - ヘルパー
  /mailers        - メール関係
  /models         - モデル
  /views          - ビュー(html)
/bin              - バイナリーファイル、コマンド実行ファイルなど
/config           - 設定ファイル
  /routes.rb      - ルーティングに関するファイル
/db               - データベースの設定ファイル
/lib              - 自作ライブラリなど
/log              - ログファイル
/public           - 静的ファイル
/test             - テスト関係のファイル
/vendor           - サードパーティのファイル
Gemfile           - 必要なgemファイルを書くファイル
```

### Routing
WIP

### MVC
WIP

### 参考HP

- [Ruby on Rails チュートリアル](https://railstutorial.jp/)
- [小学生でもわかるRuby on Rails入門](https://openbook4.me/projects/92)
- [Ruby on Rails Guides](http://guides.rubyonrails.org/)
- [Ruby on Rails API](http://api.rubyonrails.org/)
- [Rubyはじめての人がRails開発に参加するときに最初に知っておくべきこと](http://qiita.com/awakia/items/42525adb473c7cc6b811)
