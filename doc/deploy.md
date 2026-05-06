# デプロイ手順

## 構成

```
GitHub (jam006097/inoueshika-hp)
    ↓ pushで自動トリガー
Cloudflare Pages
    ↓
https://inoueshika-hp.pages.dev（または独自ドメイン）
```

## 初回セットアップ（済）

1. GitHub リポジトリ作成・初期プッシュ
2. Cloudflare Pages プロジェクト作成
3. GitHub リポジトリと連携

## 日常のデプロイ

```bash
# コード変更後
git add index.html
git commit -m "内容の更新"
git push
```

mainブランチへのpushで Cloudflare Pages が自動的にデプロイ。  
通常1〜2分で反映される。

## Cloudflare Pages の設定

| 項目 | 値 |
|---|---|
| ビルドコマンド | （空欄） |
| 出力ディレクトリ | `/`（ルートディレクトリ） |
| ブランチ | main |

## 独自ドメインを設定する場合

1. Cloudflare Pages ダッシュボード → プロジェクト → カスタムドメイン
2. 使用するドメインを入力
3. DNS設定の指示に従う（CloudflareでDNS管理していれば自動設定可）

## ロールバック

```bash
# 直前のコミットに戻す
git revert HEAD
git push
```

または Cloudflare Pages ダッシュボードの「デプロイ」タブで  
過去のデプロイを選択して「再デプロイ」。

## 確認コマンド

```bash
# ローカルで動作確認（Python が入っている場合）
python3 -m http.server 8000
# → http://localhost:8000 で確認
```
