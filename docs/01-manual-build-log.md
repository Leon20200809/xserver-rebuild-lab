# Manual Build Log

このファイルは、Xserver Rebuild Lab の手動構築ログです。

最終的に IaC 化する前に、まずは Ubuntu 上で一つずつ手作業で構築し、何をしたのか、何を理解したのかを記録します。

## 2026-06-24 現在の到達点

### WSL2 / Ubuntu

- WSL2 Ubuntu を導入した
- Windows Terminal から Ubuntu を操作できるようにした
- `wsl ~` で Ubuntu のホームディレクトリへ入れることを確認した
- `exit` で WSL から抜けられることを確認した

### Linux Directory

以下の違いを確認した。

- `/home`
  - Linux ユーザーごとの作業場所

- `/mnt/c`
  - Windows 側の C ドライブへアクセスするための通路

- `/var/www/html`
  - Apache の標準公開ディレクトリ

### Apache

- Apache2 をインストールした
- Apache2 を起動した
- `http://localhost` で Apache 初期ページを表示確認した
- Apache が HTTP リクエストを受けて HTML を返すことを確認した

### Permission

以下を体験した。

- `sudo`
- `chown`
- Linux の所有者と権限
- `/var/www/html` 配下の編集権限

### Log

Apache の access.log を確認した。

確認対象:

- アクセス元
- HTTP メソッド
- リクエストパス
- ステータスコード
- User-Agent

### PHP

- PHP 8.5 を導入した
- Apache 経由で PHP が実行されることを確認した
- `phpinfo()` により PHP 実行環境を確認した

### MySQL

- MySQL 8.4 を導入した
- MySQL の起動を確認した
- `sudo mysql` で MySQL 操作モードへ入れることを確認した
- WordPress 用データベース `wordpress` を作成した
- WordPress 用 MySQL ユーザー `wpuser` を作成した
- `wpuser` に `wordpress` データベースへの権限を付与した
- `SHOW GRANTS FOR 'wpuser'@'localhost';` で権限を確認した
- `mysql -u wpuser -p wordpress` で専用ユーザーからデータベースへ接続できることを確認した
- `SHOW TABLES;` で WordPress 未導入時点ではテーブルが空であることを確認した

### PHP / PDO / MySQL Connection

- `php-mysql` が導入済みであることを確認した
- PHP から MySQL へ PDO 接続できるか確認した
- `samples/mysql-connect.php.example` をもとに接続確認用ファイルを作成した
- Apache 経由で `http://localhost/mysql-connect.php` にアクセスした
- `MySQL connection successful.` が表示されることを確認した

## 次に行うこと

次回は以下から開始する。

1. 接続確認用の `mysql-connect.php` が `/var/www/html/` に残っている場合は削除する
2. WordPress 本体を手動で配置する
3. WordPress の `wp-config.php` に DB 情報を設定する
4. ブラウザから WordPress インストール画面を開く
5. WordPress が `wordpress` データベース内にテーブルを作成する流れを確認する
6. 手動構築ログを更新する

## 手動構築から IaC 化する予定の項目

今後、以下の作業を Ansible 化していく。

- package install
- Apache setup
- PHP setup
- MySQL setup
- WordPress DB setup
- file permission setup
- Apache VirtualHost setup
- Firewall setup
- SSL setup
- backup script setup

## Memo

手作業で一度理解してから、自動化する。

自動化は目的ではなく、理解した手順を再現可能にするための手段である。
