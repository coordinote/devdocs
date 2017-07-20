# database schema

## 概要
DBのスキーマの設計と定義

## 情報
  * 設計書作成日時
    - 2017/07/04
  * 設計書作成者
    - RS
  * 実装環境
    - nedb
  * 実装先ブランチ
    - `database`
  * 実装先
    - `nedb_module/`
  * 重要度
    - 高

## 設計

## 保存先
* 基本的に以下のディレクトリに配置される
  - `/path/to/home/.coordinote/database/`
* ファイル名に関する記述は`collection_split.md`にて

## clip_schema
+ `date`
  - 型: date-time
  - 作成日時(登録日時)
+ `tile_file`
  - 型: string
  - タイル保存先ファイル名
+ `tag`
  - 型: array
  - タグ(複数)
+ `_id`
  - 型: string
  - 自動追加

## tile_schema
+ `cid`
  - 型: string
  - 対応clipドキュメントの`_id`要素
+ `idx`
  - 型: integer
  - インデックス
+ `col`
  - 型: integer
  - カラムサイズ
+ `tag`
  - 型: array
  - タグ(複数)
+ `sty`
  - 型: string(enum)
    - txt
      - プレーンテキスト
    - svg
      - svgデータ
    - fig
      - イメージバイナリ
  - タイルスタイル
+ `con`
  - 型: string
  - コンテンツ
+ `_id`
  - 型: string
  - 自動追加

## 備考
* 以上はファイル的スキーマ定義であり，論理的なスキーマは以下のとおりである

+ `date`
+ `tile_file`
+ `tag`
+ `_id`
+ `tile(array)`
  + `cid`
  + `idx`
  + `col`
  + `tag`
  + `sty`
  + `con`
  + `_id`

