# Xserver Rebuild Lab

Xserver Rebuild Lab は、Xserver のようなレンタルサーバー環境で提供される Apache / PHP / MySQL / WordPress 実行環境を、Ubuntu 上で手動構築し、最終的に IaC として再現可能にする学習・検証プロジェクトです。

## Goal

最終目標は、VPS や AWS 上に Ubuntu を用意したあと、Ansible などの YAML を実行することで、WordPress が動作する Web 公開環境を再現できる状態にすることです。

つまり、単に WordPress を使うのではなく、WordPress が動くサーバー環境そのものを理解し、構築し、自動化します。

## Current Status

現時点では、WSL2 Ubuntu 上で以下の土台を手動構築しています。

- WSL2 Ubuntu 導入
- Windows Terminal 運用開始
- `/home`、`/mnt/c`、`/var/www/html` の違いを確認
- Apache2 導入
- `http://localhost` で Apache 初期ページ表示確認
- Linux 権限、`sudo`、`chown` の基礎確認
- Apache access.log の読み方確認
- PHP 8.5 導入
- Apache 経由で PHP 実行確認
- MySQL 8.4 導入
- MySQL 起動確認

## Next Step

次に行う作業は以下です。

- `sudo mysql` で MySQL 操作モードへ入る
- WordPress 用 database を作成する
- WordPress 用 MySQL user を作成する
- WordPress 用 user に必要な権限を付与する
- PHP から MySQL へ接続確認する

## Future Plan

今後、この手動構築手順を整理し、以下のように IaC 化していきます。

- Apache インストール
- PHP と必要拡張のインストール
- MySQL インストール
- WordPress 用 DB / user / 権限作成
- Apache VirtualHost 設定
- SSH 設定
- Firewall 設定
- SSL 証明書設定
- Backup / Restore 設計
- Ansible 化
- GitHub Actions 連携

## Repository Policy

このリポジトリには、サーバーを再現するための設計図、手順書、検証用サンプル、自動化ファイルを置きます。

秘密情報は絶対にコミットしません。

コミットしないものの例:

- 本物のパスワード
- 秘密鍵
- `.env`
- 実運用中の `wp-config.php`
- 本番 DB の dump
- 個人情報を含むログ

## Concept

サーバーを借りるだけで終わらせない。

Web 公開環境の裏側を理解し、再現し、最終的にはコードで召喚できる状態にする。
