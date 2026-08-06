<a id="data-analytics-dataquery-release-notes"></a>
## Data & Analytics > DataQuery > リリースノート { #data-analytics-dataquery-release-notes }

<a id="may-27-2026"></a>
## 2026. 05. 27. { #may-27-2026 }

<a id="added-integration-services"></a>
### 連携サービスの追加 { #added-integration-services }

* データソースのタイプにData Lake Storageを追加しました。
<a id="april-28-2026"></a>
## 2026. 04. 28. { #april-28-2026 }

<a id="april-28-2026-added-integration-services"></a>
### 連携サービスの追加 { #april-28-2026-added-integration-services }
* Cloud Schedulerサービスに「予約されたクエリ」テンプレートを追加しました。
  * テンプレートを使用して、クエリを任意のスケジュールで実行できます。

<a id="march-24-2026"></a>
## 2026. 03. 24. { #march-24-2026 }

<a id="feature-updates"></a>
### 機能改善・変更 { #feature-updates }
* コンソールクエリ結果の表示ポリシーを改善
  * コンソールで実行したクエリ結果を1MB、5,000行以内で表示していた制限を削除しました。
  * コンソールで実行したクエリ結果を最大30MBまで表示できるように改善しました。
  * コンソールクエリ結果を照会し、コピーするボタンを追加しました。
  
<a id="september-23-2025"></a>
## 2025. 09. 23. { #september-23-2025 }

<a id="trino-version-upgrade"></a>
### Trinoバージョンのアップグレード { #trino-version-upgrade }
* DataQueryのサービス基盤をTrino 476バージョンにアップグレードしました。
* これには、一部のクエリにおけるパフォーマンス向上とバグ修正が含まれています。

<a id="june-24-2025"></a>
## 2025. 06. 24. { #june-24-2025 }

<a id="added-features"></a>
### 機能追加 { #added-features }
* クラスターの状態指標視覚化領域を追加しました。
  * 2025年6月24日以降に開始されたクラスターの状態を収集します。
  
<a id="may-27-2025"></a>
## 2025. 05. 27. { #may-27-2025 }

<a id="may-27-2025-added-features"></a>
### 機能追加 { #may-27-2025-added-features }
* Object Storageデータソースと連動するためのメタストアのインスタンスタイプを設定する機能を追加しました。

<a id="january-21-2025"></a>
## 2025. 01. 21. { #january-21-2025 }

<a id="january-21-2025-feature-updates"></a>
### 機能改善・変更 { #january-21-2025-feature-updates }
* DataQueryをTrino 462バージョンに基づいてサービスするようにアップグレードしました。
* iceberg connectorに関するadd_files_with_partition関数を追加しました。

<a id="october-29-2024"></a>
## 2024. 10. 29. { #october-29-2024 }

<a id="october-29-2024-trino-version-upgrade"></a>
### Trinoバージョンのアップグレード { #october-29-2024-trino-version-upgrade }
* DataQueryをTrino 455バージョンをベースにサービスするようにアップグレードしました。
* 一部のクエリの性能向上とバグ修正が含まれています。

<a id="october-29-2024-added-features"></a>
### 機能追加 { #october-29-2024-added-features }

* データソースタイプにIcebergを追加しました。

<a id="july-23-2024"></a>
## 2024. 07. 23. { #july-23-2024 }

<a id="july-23-2024-feature-updates"></a>
### 機能改善・変更 { #july-23-2024-feature-updates }
* クエリ履歴を保存するためのObject Storage認証情報の有効期限が切れると、連動無効化案内メールが送信されるようになりました。

<a id="june-25-2024"></a>
## 2024. 06. 25. { #june-25-2024 }

<a id="june-25-2024-added-features"></a>
### 機能追加 { #june-25-2024-added-features }
* データソースタイプにMariaDBが追加されました。
* クエリ履歴保存機能が追加されました。

<a id="may-28-2024"></a>
## 2024. 05. 28. { #may-28-2024 }

<a id="may-28-2024-feature-updates"></a>
### 機能改善・変更 { #may-28-2024-feature-updates }
* クエリ情報の保存期限を90日に変更しました。

<a id="may-1-2024"></a>
## 2024. 05. 01. { #may-1-2024 }

<a id="may-1-2024-feature-updates"></a>
### 機能改善・変更 { #may-1-2024-feature-updates }
* Object Storageデータソースの最大登録制限を5個に変更しました。
* Object Storageデータソースの最小登録制限を削除しました。

<a id="february-27-2024"></a>
## 2024. 02. 27. { #february-27-2024 }

<a id="february-27-2024-feature-updates"></a>
### 機能追加 { #february-27-2024-feature-updates }
* ユーザーがよく使うクエリを保存・管理できる機能が追加されました。

<a id="january-23-2024"></a>
## 2024. 01. 23. { #january-23-2024 }

<a id="january-23-2024-trino-version-upgrade"></a>
### Trinoバージョンのアップグレード { #january-23-2024-trino-version-upgrade }

* DataQueryで提供するTrinoバージョンが398から434にアップグレードされました。
* データソースのタイプにPostgreSQL、Oracle、EDBが追加されました。

<a id="october-31-23"></a>
## 2023. 10. 31. { #october-31-23 }

<a id="october-31-23-feature-updates"></a>
### 機能改善・変更 { #october-31-23-feature-updates }
* クラスタタイプ選択機能を追加しました。

<a id="december-27-2022"></a>
## 2022. 12. 27. { #december-27-2022 }

<a id="release-of-a-new-service"></a>
### 新規サービスのリリース { #release-of-a-new-service }

* 分散SQLクエリエンジンTrinoを使って大規模データに対してクエリを実行できるサービスです。
* データソースとしてNHN Cloud Object Storage、NHN Cloud RDS for MySQLをサポートします。
