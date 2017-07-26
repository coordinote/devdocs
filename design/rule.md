# coordinote rule
## Branch
- `export_screen`, `edit_screen`, `settings_screen` に各々のコミットをプッシュ
- 各screenの開発終了時に screen Branch に Pull request
- Pull request はリクエスト者以外がレビュー後merge
- Branch を増やす場合は、わかりやすい名前または役割の報告(Slack)

## Dirname
- 画面に関しては、 `export_screen`, `edit_screen`, `settings_screen` とする

## main.js
- ウィンドウの生成等はこれを用いる
- 変更は基本的になし(必要な場合は要相談)
- `file://` プロトコルを使用する場合のパスはgitプロジェクトからの絶対パスを指定
    - 例 : `<script src="./js/hoge.js">`  →  `<script src="/__dirname/hoge_screen/js/hoge.js">`
- 但し，htmlファイルの転送については `__dirname` を接頭したgitプロジェクトからの絶対パスを指定
    - 例 : `pathname: __dirname + '/path/to/file.html'`

## LICENSE
- The MIT LICENSE を使用
- 他LICENSEの侵害に注意

## package
- package 追加時、`npm install <hoge> --save` の方式に従ってインストールを行う
- 追加後、他メンバーは `npm install` を実行

## resource
- image等の挿入物はすべてresource内で管理する

## Version
- node.js 6.10.1 を使用

## screen-move
- 画面遷移の際は、`ipcRenderer.send(PATH_DATA.event, PATH_DATA.<hoge>)` を使用すること
- 各々の PATH_DATA は `common.js` を参照

## require & common
- 各々はこれを `head` タグで読み込むこと
  - `<script type="text/javascript" src="/__dirname/require.js"></script>`
  - `<script type="text/javascript" src="/__dirname/common.js"></script>`
- 変更の際は要相談

