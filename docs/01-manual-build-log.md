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

## 次に行うこと

次回は以下から開始する。

```bash
sudo mysql
```

その後、以下を行う。

1. WordPress 用 database を作成する
2. WordPress 用 MySQL user を作成する
3. WordPress 用 user に database 権限を付与する
4. PHP から MySQL 接続確認を行う

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
