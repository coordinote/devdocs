# Edit Screen UI

## 概要

## 情報
  * 設計書作成日時
    - 2017/05/04
  * 設計書作成者
    - RS
  * 実装環境
    - gulp
    - gulp-less
  * 実装先ブランチ
    - `screen/edit_screen/edit_ui`
  * 実装先ファイル
    - `edit_screen/edit.html`
    - `less/`
    - `js/`
  * 重要度
    - 高

## 設計

### データ受取方法, 受渡し方法, etc.
* このページをAngular2 に渡してtemplateに記述させる
* `clip-view`
  - 今回書いているノートのリストを表示する部分
* `write-view`
  - 現在書いているノートの編集部分

### 主なプロセス
* html5とless(css)，jsを用いてページを記述
* Angular2にviewとしてhtmlを読み込ませる
* templateを用いて，`clip-view`，`write-view`にデータを表示させていく

### メソッド(関数)
* なし(jsに各種)

### フィールド(変数)
* なし(jsに各種)

## 備考
* `edit_screen`はAngular2サーバにアクセスすることで表示される
* 静的ページによる提供は行わない

