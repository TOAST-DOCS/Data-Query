<!-- pre-align:aligned sig=9a93e7290804 -->

<a id="dataquery-overview"></a>
## DataQuery概要 { #dataquery-overview }

* 分散SQLクエリエンジンTrinoを使って大規模データに対してクエリを実行できるサービスです。
* Object StorageなどNHN Cloudサービスとの連動をサポートします。

<a id="main-features"></a>
## 主な機能 { #main-features }

* NHN Cloud Object Storage、NHN Cloud RDS for MySQLなどのデータソースへの接続をサポートします。
* それぞれ異なるデータソースに対して標準SQLで統合クエリ実行が可能です。
* Webコンソール内でクエリ実行が可能です。
* Webコンソールクエリ結果のプレビューおよびダウンロード機能を提供します。
* 実行中または完了したクエリの情報およびヒストリーを提供します。
* Trinoエンドポイントを介してUI接続および外部ツール(JDBC、CLI、BIソリューションなど)との連動が可能です。
* ユーザープロジェクトごとにTrinoクラスタを提供し、必要な時は仕様の調節が可能です。

<a id="service-terminology"></a>
## サービス用語 { #service-terminology }

| 用語 | 説明 |
| --- | --- |
| データソース | DataQueryで使用するためのデータベースまたはデータセットを意味します。 |
| カタログ | スキーマを含み、コネクタを介してデータソースを参照する役割を担います。 |
| スキーマ | テーブルを構成し、カタログと一緒にクエリ可能なテーブルを定義します。一般的なRDBMSでのDBと同じ概念です。 |
| テーブル | 行と列で構成されるデータの集合です。 |
| クラスタ | Trinoクラスタを意味します。 |
