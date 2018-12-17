# src/

## Directories

各ディレクトリ構成は以下の通り。

| Direcotry | Description                                             |
|-----------+---------------------------------------------------------|
| core/     | いわゆるモデル                                          |
| api/      | WEB API                                                 |
| web/      | 認証されたセッションのみ配布する静的ファイルなど        |
| front/    | Riot.js で作るフロントエンド。View を作る               |
| db/       | Database を使うためのコード                             |
| data/     | これはいらん気がする。                                  |
| docs/     | このプロジェクトのマニュアル riot-template とかで作る。 |

## Nginx の設定

こんな感じにする。

`*.js` なファイルは認証されたセッションにのみリクエストを返す感じ。

```
location /assets/ { alias /your/prj/path/front/assets/; }
location /libs/   { alias /your/prj/path/front/libs/; }
location /js/     { proxy_pass http://localhost:55555; }
location /        { proxy_pass http://localhost:55555; }
location /data/   { alias /your/prj/path/data/; }
```
