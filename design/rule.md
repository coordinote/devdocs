# coordinote rule
## Branch
- main, pdf, edit, settings_screen に各々のコミットをプッシュ
- 各screenの開発終了時に screen Branch に Pull request
- Pull request はリクエスト者以外がmerge
- Branch を増やす場合は、わかりやすい名前または役割の報告(Slack)
- 何らかの重要な修正が必要な場合は、main_fix へ pull request

## Dirname
- 画面に関しては、main, pdf, edit, settings_screen とする

## main.js
- ウィンドウの生成等はこれを用いる
- 変更は基本的になし(必要な場合は要相談)
- 'file:' プロトコルを使用する場合のパスはgitプロジェクトからの絶対パスを指定
    - 例 : `<script src="./js/hoge.js">`  →  `<script src="/hoge_screen/js/hoge.js">`
- 但し，htmlファイルの転送については `__dirname` を接頭したgitプロジェクトからの絶対パスを指定
    - 例 : `pathname: __dirname + '/path/to/file.html'`

## LICENSE
- The MIT LICENSE を使用
- 他LICENSEの侵害に注意

## package
- package 追加時、`npm install <hoge> --save-dev` の方式に従ってインストールを行う
- 追加後、他メンバーは `npm install` を実行

## resource
- image等の挿入物はすべてresource内で管理する

## Version
- node.js 6.10.1 を使用

## Navigation menu
- 共通の navigation menu を使用する

## screen-move
- 画面遷移の際は、`ipcRenderer.send(PATH_DATA.event, PATH_DATA.<hoge>)` を使用すること
- 各々の PATH_DATA は screen_info.json を参照

## screen_info.json
- 変更又は追加の際は報告し、pull request を main_fix へ飛ばす

## semantic-ui
- semantic-ui の読み込みは `head` タグで読み込むこと
    - cssの読み込み : `<link rel="stylesheet" href="/node_modules/semantic-ui/dist/semantic.min.css" />`
    - jsの読み込み : `<script src="/node_modules/semantic-ui/dist/semantic.min.js"></script>`

## require & common
- 各々はこれを `head` タグで読み込むこと
    - `<script type="text/javascript" src="/require.js"></script>`
    - `<script type="text/javascript" src="/common.js"></script>`
- 変更の際は要相談

