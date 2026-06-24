# Goal

## このプロジェクトの目的

このプロジェクトの目的は、Xserver のようなレンタルサーバーで裏側に用意されている Web 公開環境を、Ubuntu 上で自力構築し、最終的に IaC として再現できるようにすることです。

## 再現したい環境

主に以下の構成を再現対象とします。

- Linux
- Apache
- PHP
- MySQL
- WordPress
- SSH
- 権限管理
- ログ確認
- Firewall
- HTTPS / SSL
- Backup / Restore
- IaC / Ansible

## なぜ作るのか

Xserver などのレンタルサーバーでは、Apache、PHP、MySQL、SSL、権限、ログなどの多くの設定が管理画面の裏側で処理されています。

このプロジェクトでは、その裏側を手作業で再現することで、Web サーバーの構造を理解します。

最終的には、その手作業を Ansible などの YAML に落とし込み、VPS や AWS 上の Ubuntu に対して再現可能な構築手順にします。

## MVP

最初の MVP は、以下を達成した状態とします。

- Ubuntu 上で Apache が動作する
- Apache 経由で PHP が実行できる
- MySQL が起動している
- WordPress 用 DB と user を作成できる
- PHP から MySQL へ接続確認できる
- 手動構築ログが残っている

## 最終形

最終形は以下です。

1. VPS または AWS に Ubuntu を用意する
2. SSH で接続できるようにする
3. GitHub リポジトリにある IaC を実行する
4. Apache / PHP / MySQL / WordPress 実行環境が構築される
5. README を読めば、構成・手順・思想が分かる
