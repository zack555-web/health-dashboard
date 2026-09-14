# Personal Dashboard

## ページ構成

- `/index.html`：サイト全体の入口（Personal / Test）
- `/personal/index.html`：Main Dashboard（集計表示は今後追加）
- `/personal/health/index.html`：Health Dashboard
- `/personal/english/index.html`：英語学習Dashboard（準備中）
- `/personal/food/index.html`：食事管理（未定）
- `/test/index.html`：Web制作テスト
- `/data/health-data.json`：Healthデータの唯一の更新先

公開先リポジトリは `zack555-web/zack555-web.github.io`。元の `health-dashboard` リポジトリを、履歴・ブランチを保持して改名しています。

## 公開URL

- サイト：https://zack555-web.github.io/index.html
- Main：https://zack555-web.github.io/personal/index.html
- Health：https://zack555-web.github.io/personal/health/index.html
- English：https://zack555-web.github.io/personal/english/index.html
- データ：https://zack555-web.github.io/data/health-data.json

Healthは `../../data/health-data.json` を読みます。Health / English / Foodの戻るリンクは `../index.html`（Main）です。Mainの戻るリンクはサイト全体の入口です。

## Shortcut（未運用）

今後の読み書きには次のGitHub Contents APIを使います。

`https://api.github.com/repos/zack555-web/zack555-web.github.io/contents/data/health-data.json`

GETは `?ref=main`。PUTには `branch: main`、GETで取得したこのファイルの最新 `sha`、Base64化したJSONを `content` に指定します。旧ファイルのSHAは流用しません。認証情報はShortcut側に保持し、公開リポジトリに置きません。実機でのShortcut実行確認は未実施です。

## 旧URLの互換性

`/health-dashboard/index.html` と `/health-dashboard/` は新しいMainに案内します。旧Health / English / Food / TestのHTML URLは `404.html` で対応する新URLへ転送します（JavaScript有効時）。通常の存在しないURLは404のままです。

`/health-data.json`、`/health-dashboard/health-data.json`、`/health-dashboard/data/health-data.json` は移行時の固定スナップショットです。自動同期しません。更新は必ず `/data/health-data.json` に行ってください。`health-dashboard/` は旧リンク互換用のみで、Dashboard本体は置きません。

## バックアップ・復旧

最初の移行前：`c81089dfc17a065a4c0f95f63836ac271e42d8c1`（`codex/backup-before-personal-20260914`）。

今回の配置修正前：`97b2d1220f68c81ad30cd15a607a68797b45f855`。初回移行の内容は `codex/personal-dashboard` ブランチにも残っています。

Healthデータと既存の表示項目は変更していません。復旧時には、まず移行後に追加されたデータを別途保存してください。UI修正を戻す場合は該当PRのマージをrevertします。リポジトリ全体を古い状態へresetすると後日のデータが失われるため避けてください。公開URLを旧形式へ戻すには、ファイルのrevertだけでなくリポジトリ名とPagesの公開元も別途確認する必要があります。
