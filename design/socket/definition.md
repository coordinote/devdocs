# socket定義

## 概要
socket通信の使用方法

## 定義
socketのイベント名は"'emit側から見て行う処理'\_'受け渡しするデータの概要'"  
サーバー側のsocketで受け取ったデータはすべてrecとする

### emit側から見て行う処理
- send
  - データを送る際に使用するイベント
- save
  - データベースにデータを保存する場合に使用
- get
  - データは送らないがデータがほしい場合に使用する
- res
  - send,reqに対してデータを返す場合に使用する
- update
  - DBのアップデート処理
- delete
  - DBの削除処理
### 受け渡しするデータの概要
何のデータかわかるようにすれば特に指定しない。

## イベント
- send_connect
  - serverへのコネクション情報の送信
- send_writeconnect
  - canvasのwriteがコネクトしたという情報の送信
- send_readconnect
  - canvasのreadがコネクトしたという情報の送信
- res_reloadevent
  - ページの更新イベントを返す
- send_pathdata
  - canvasのパスのデータの送信
- res_pathdata
  - canvasのパスのデータを返す
- send_beforeevent
  - canvasのbeforeイベントの送信
- res_beforeevent
  - canvasのbeforeイベントを返す
- send_afterevent
  - canvasのafterイベントの送信
- res_afterevent
  - canvasのafterイベントを返す
- save_clip
  - clipのセーブ
- res_cid
  - saveされたclipのcidを返す
- save_tile
  - tileのセーブ
- rec_tid
  - saveされたtileのtidを返す
- get_allcliptags
  - すべてのタグを要求する
- res_allcliptags
  - すべてのタグを返す
- send_clipsearchdata
  - clipの検索データの送信
- res_alltiletags
  - 検索結果に沿ったタイルのタグを返す
- res_clips
  - 検索結果に沿ったクリップを返す
- send_tilesearchdata
  - tileの検索データの送信
- res_tiles
  - 検索結果に沿ったタイルを返す
- update_tiletag
  - タイルのタグのアップデート
- update_tilecon
  - タイルコンテンツのアップデート
- update_tilecol
  - タイルのカラムサイズのアップデート
- update_tileidx
  - タイルインデックスのアップデート
- delete_clip
  - クリップの削除
- delete_tile
  - tileの削除
- update_cliptags
  - cliptagのアップデート
