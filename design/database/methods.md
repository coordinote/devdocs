# DB メソッド

## 概要
DBのメソッドと使用方法に関する設計

## 情報
  * 設計書作成者
    - RS
  * 実装環境
    - nedb
  * 実装先ブランチ
    - `database`
  * 実装先
    - `database/`
  * 重要度
    - 高

## 設計

### データ受取方法, 受渡し方法, etc.
* `/path/to/coordinote/database/nedb_module.js`をrequire
* requireしたオブジェクトのインスタンスを`new` で作成
* 作成したインスタンスからメソッドを実行
* 引数の最後のコールバック関数に戻り値を代入する

### 主なプロセス
* `Node.js` オブジェクトのrequireに準拠
* `nedb` のクエリメソッドを使用
* マスタースレーブ方式
  - 複数のDBファイルの検索結果を連結して1つのオブジェクトとする
  - 連結したオブジェクトをコールバック関数の引数に入れる

### メソッド(関数)

#### insert
* `insert_clip(tag, callback)`
  - `tag`: 型: array, クリップのタグ
  - `callback`: 型: function, 関数の第1引数に生成されたドキュメント(型: object)
* `insert_tile(instance, callback)`
  - `instance`: 型: object, `cid`, `idx`, `col`, `tag`, `sty`, `con`で構成
    - `cid`: 型: string, 対応するclipのドキュメントの`_id`
    - `idx`: 型: integer, タイルのインデックス
    - `col`: 型: integer, タイルのカラムサイズ
    - `tag`: 型: array, タイルのタグ
    - `sty`: 型: string, {`txt`, `svg`, `fig`}のいずれかを記述, タイルの種類
    - `con`: 型: string, タイルのコンテンツ
  - `callback`: 型: function, コールバック関数の第1引数に生成されたドキュメント(型: object)

### find
* `find_clip_id(id, callback)`
  - `id`: 型: string, 検索対象クリップの`_id`
  - `callback`: 型: function, 関数の第1引数にクリップ + 対応する全てのタイルドキュメント(型: object)
* `find_tiles_cid(cid, callback)`
  - `cid`: 型: string, 検索対象タイルの`cid`
  - `callback`: 型: function, 関数の第1引数に対応する全てのタイルドキュメント(型: array)
* `find_allclipstags(callback)`
  - `callback`: 型: function, 関数の第1引数に全 `clip` の登録済み `tag` (型: array)
* `find_clips_tags(clip_tags, callback)`
  - `clip_tags`: 型: array, `tag`要素での検索ワード
  - `callback`: 型: array, 関数の第1引数に該当する`clip` (型: array)
* `find_alltilestags_cid(cid, callback)`
  - `cid`: 型: string, 検索対象タイルの`cid`
  - `callback`: 型: function, 関数の第1引数に対応する全 `tile` の登録済み `tag` (型: array)
* `find_tiles_cidtags(cid, tile_tags, callback)`
  - `cid`: 型: string, 検索対象タイルの`cid`
  - `tile_tags`: 型: array, `tag`要素での検索ワード
* `find_clipids_tags(clip_tags, s_date, e_date, callback)`
  - `clip_tags`: 型: array, `tag`要素での検索ワード
  - `s_date`: 型: Date, 検索開始の日付
  - `e_date`: 型: Date, 検索終了の日付
  - `callback`: 型: function, 関数の第１引数に対応する全 `clip` の `_id` (型: array)

#### update

#### delete

### フィールド(変数)
* なし(jsに各種)

## 備考
* テストコード(`/path/to/coordinote/database/test/` 以下)を参照
* `insert_clip()`のサンプルコードを以下に記述

```
const NeDB_Module = require('/path/to/coordinote/database/nedb_module.js')  
let nedb_module = new NeDB_Module()  
nedb_module.insert_clip(['test', 'coordinote'], (newdoc) => {  
  console.log(newdoc)  
})  
```
