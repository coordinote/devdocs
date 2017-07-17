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

### 受け渡しするデータの概要
何のデータかわかるようにすれば特に指定しない。

## イベント
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
- get_alltags
  - すべてのタグを要求する
- res_alltags
  - すべてのタグを返す
- send_connect
  - serverへのコネクション情報の送信
- send_writeconnect
  - canvasのwriteがコネクトしたという情報の送信
- send_readid
  - canvasのreadのidの送信
- res_reloadevent
  - ページの更新イベントを返す
