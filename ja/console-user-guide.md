## Data & Analytics > DataQuery > コンソール使用ガイド

DataQueryサービスを使用するには、必ずデータソースを追加する必要があります。
以下のような手順でサービスを使用できます。

* 連動するデータソース追加
* データソースを反映するためのクラスタ起動
* Webコンソールのクエリエディタまたは外部接続URLを介した別途ツールでのクエリ実行

## データソース

### データソース追加

* データソース設定および反映制約事項
    * Object Storageタイプのデータソースが存在している時のみ他のデータソースを追加できます。
    * Object Storageタイプのデータソースが存在する時のみクラスタを有効にしてクエリを実行できます。
    * Object Storageタイプのデータソースは1つだけ登録できます。
* **データソースの追加**をクリックします。

#### Object Storageデータソースタイプ

* **データソース追加**をクリックし、ダイアログボックスにObject Storage情報を入力します。
    * データソース名
        * クエリ実行時に使用されるセパレータで、データソース間で一意の値なければなりません。
    * アクセスキー、秘密鍵、リージョン
        * 連動するデータが存在するObject Storageの接続情報です。
        * アクセスキーと秘密鍵はObject Storageコンソールで発行できます。詳細については[Object Storageコンソール使用ガイド](https://docs.toast.com/ko/Storage/Object%20Storage/ko/console-guide/#s3-api)をご覧ください。
        * リージョンはObject Storageガイドのリージョン別[S3リージョン](https://docs.toast.com/ko/Storage/Object%20Storage/ko/s3-api-guide/#aws-cli)をご覧ください。
    * バケット名
        * システムで基本テーブル情報や管理テーブル情報、データを保存するために使用するObject Storageコンテナ名(dataquery-warehouse)です。
            * 独自にdataquery-warehouseコンテナを作成して使用します。
        * 連動する既存データは、dataquery-warehouseコンテナ外部に存在できます。
* その他の事項
    * 連動するObject Storageは、同じNHN Cloudプロジェクト外部に存在できます。
> [注意]
> DataQueryと連動するObject Storageが同じリージョンではない場合、ネットワークトラフィックによる追加料金が発生する可能性があります。

#### MySQLデータソースタイプ

* データソース名
        * クエリ実行時に使用されるセパレータで、データソース間で一意の値でなければなりません。
* 接続URL
    * MySQLデータベース接続アドレスです。
    * **jdbc:mysql://[ホスト、ip]:[ポート]?[パラメータ]**フォーマットで入力する必要があります。
    * 必ずタイムゾーンを設定する必要があります。
        * ex) jdbc:mysql://localhost:10000?**serverTimezone=Asia/Seoul**
* ユーザーID
    * 接続するMySQLアカウント名です。
* パスワード
    * 接続するMySQLパスワードです。

## クエリエディタ

* クエリエディタはクラスタ領域、スキーマ領域、エディタ領域、結果/コンソール実行領域nに区分されます。

<img src="https://static.toastoven.net/prod_dataquery/dataquery_console_01_en.png"/>

### 1. クラスタ領域

* クラスタのオン/オフを切り替えることができます。
* 追加、変更、削除したデータソース情報を実際の動作に反映させるにはDataQueryクラスタを再起動する必要があります。
* データソースの追加または変更、削除などの動作があった場合、以下のようにクラスタ再起動文言が表示されます。
    * Object Storageは必須データソースであり、Object Storageデータソースが削除されるとクラスタの起動ができません。
* クラスタの電源を切るのに1～2分、電源を入れるのに3～4分程度の時間がかかることがあります。
* DataQueryクラスタはすべてのデータソースを反映し、個別のデータソース適用はできません。
* 継続的にクラスタの**オン/オフ**に失敗する場合は、サポートにお問い合わせください。

### 2. スキーマ領域

* 接続設定されたデータソースと、該当ソースで提供する実際のDB 、テーブル、カラム情報を確認できます。
    * information\_schemaはデータソースとの接続情報を持っているDBで、ユーザーが任意にデータを操作できません。
* 各項目の更新アイコンをクリックして、データソース、スキーマ、テーブル、カラム情報を新しく取得できます。
    * ただし、上位スキーマを更新しても下位情報は全部新しく読み込みません。テーブルを更新する場合、テーブルリストのみ新たに取得し、各テーブルのカラム情報はアップデートされません。

### 3. エディタ領域

* **\+ クエリ追加**をクリックしてクエリエディタを最大10個まで作成できます。
* **実行**をクリックするか、**ctrl + enter**を入力してクエリを実行でき、エディタ下部で実行中のクエリの進行状態と失敗時の原因ログを確認できます。
* クエリ作成時に収集されたデータソース、スキーマ、テーブル、カラム名のオートコンプリートをサポートします。

#### SQLガイド

* DataQueryのSQLはTrino基準に従って動作します。
    * Trinoは標準SQL文法(ANSI SQL)に従います。
    * Trinoは、独自にデータを持たず、複数のデータソースとの連動によりデータを処理します。
        * データソースごとに例外的な文法や制約事項が存在する場合があります。
    * トランザクション処理(OLTP)作業ではなく、分析処理(OLAP)作業に合わせて設計されました。
* データ型
    * BOOLEAN、整数型、小数点、文字列、日付、UUID、ハイパーログなどのタイプをサポートします。
* Trinoクエリ
    * DDL(Data Definition Language、データ定義語)、DML(Data Manipulation Language、データ操作語)をサポートし、以下の追加構文をサポートします。
        * メタデータを確認できる構文：SHOW CATALOGS、SHOW SCHEMAS、SHOW TABLES、SHOW STATS FOR
        * システムの内蔵プロシージャ(Procedure)を確認したりクエリの実行計画を確認したりできる構文：CALL、EXPLAIN
* 詳細については、Trinoのガイド文書をご覧ください。
    * [キーワード、データ型](https://trino.io/docs/398/language.html)
    * [Trinoクエリ](https://trino.io/docs/398/sql.html)
    * [組み込み関数](https://trino.io/docs/398/functions.html)

### 4. 結果/コンソール実行クエリ領域

* クエリエディタで実行されたクエリ結果を確認できます。
    * データサイズに応じて約1MBまたは約5,000個程度の制限された結果を提供します。
    * クエリ結果は最大30MBまでダウンロードできます。
        * Trinoを直接連動(ex. JDBC、CLI)すると、クエリ実行結果全体のデータを取得できます。設定メニューガイドをご覧ください。
        * クエリ結果はクエリ完了時刻から最大7日までダウンロードできます。12月1日13時53分32秒にクエリ実行が完了した場合、12月8日13時53分32秒の前までダウンロードできます。
    * マウス右クリックしてコンソールクエリ結果のコピー、エクスポートを実行できます。
* クエリエディタで実行したクエリリストを提供します。

<img src="https://static.toastoven.net/prod_dataquery/dataquery_console_02_en.png"/>

* ①クエリ履歴をクリックします。
* ②該当クエリが入力されたクエリウィンドウが追加作成されます。

## クエリ履歴

* 実行したクエリ情報を**クエリ履歴**画面で確認できます。
* 一番右の列の展開ボタンをクリックしてクエリの追加の実行情報を確認できます。**ダウンロード**をクリックしてクエリの全体実行情報をダウンロードできます。
    * ダウンロードファイルにクエリ結果は含まれません。

<img src="https://static.toastoven.net/prod_dataquery/dataquery_console_03_en.png"/>

## 設定

### クラスタ設定
* クラスタに設定されているインスタンスタイプとノード数を確認できます。
    * タイプについての説明や設定で提供されるリスト以外のタイプは、[サービス別料金](https://www.nhncloud.com/kr/pricing/by-service?c=Data%20%26%20Analytics&s=DataQuery)で確認できます。
* インスタンスタイプとワーカー 数を変更できます。
    * ワーカー数は最小1個から最大5個まで設定できます。
    * 設定はクラスターがオフの状態(OFF)でのみ修正できます。

### 外部連動

* 外部ツール(JDBC、CLI、BIソリューションなど)と連動できるようにTrinoエンドポイントを提供し、**設定**ページで提供する情報を利用して連動できます。
* エンドポイント接続には、個人別の認証情報が必要で、**設定**メニューで**認証キー**発行をクリックして発行できます。
    * 個人別の認証情報は、IDと認証キーで構成されており、エンドポイントに接続する時、ユーザー名(ID)とパスワード(認証キー)として活用されます。
    * パスワード(認証キー)は、最初の発行時にのみ確認できます。認証キーを紛失した場合は**認証キーの再発行**をクリックして新しい認証キーを発行する必要があります。
    * 発行/再発行された認証キーは発行してから5分後に使用できます。
* 認証情報が発行された場合はTrinoエンドポイント接続情報が画面下部に有効になります。

## データソース詳細ガイド

### Object Storageデータソースクエリ実行

* Object Storageデータソースに対するクエリは、Trino-Hiveに基づいて実行されます。
    * Hiveは[Apache Hadoop](https://hive.apache.org/)分散ストレージ環境でSQL作業処理をサポートするためのソリューションです。
* DataQueryではObject StorageアクセスのためにS3互換レイヤーを使用し、スキーマまたはテーブルのためのデータパス指定時、s3aプロトコルを使用する必要があります(ex. s3a://example/test).
* Object Storage上のParquet、JSON、ORC、CSV、Textタイプのデータに対する処理をサポートします。
* Object Storageデータソースはdefaultという名前の基本スキーマを提供し、そのスキーマで作業できます。

#### Hive機能動作のための追加の文法

* Trino-Hiveは基本的に標準SQL文法に従いますが、Hive動作対応のための追加の機能/文法が存在します。 [詳細情報](https://trino.io/docs/398/connector/hive.html#examples)
* サポートデータフォーマット
    * 基本フォーマットはORCに指定されており、設定でParquet、JSON、ORC、CSV、Textなどを指定できます。
    * テーブル作成時、with節のformat値で指定できます。

``` sql
 CREATE TABLE sample (...) WITH ( format = 'タイプ')
```

* テーブルの種類
    * 内部テーブル(Managed Table)
        * DB作成時に指定された特定パスで(dataquery-warehouseバケット)テーブルデータが管理されます。
        * テーブルを削除するとテーブル情報およびObject Storageに保存されたファイルも一緒に削除されます。
        * テーブルを作成する時、別のオプションを指定しない場合、内部テーブルとして作成されます。
    * 外部テーブル(External Table)
        * ユーザーが指定した別のパスにあるデータに基づいて動作します。
        * テーブルを削除すると、内部テーブルとは異なり接続されたデータ原本は削除されません。
        * テーブルを作成する時、WITH節のexternal\_locationにデータのパスを指定する必要があります。
          * external_locationデータのパス入力時、バケット(コンテナ)名は[NHN Cloud Object Storageのバケット命名ルール](https://docs.toast.com/ko/Storage/Object%20Storage/ko/s3-api-guide/#_7)を守る必要があります。

``` sql
# Managed Tableサンプル
 CREATE TABLE sample (...);
# External Tableサンプル
 CREATE TABLE sample (...) WITH ( external_location = 's3a://<バケット、コンテナ名>/<データディレクトリパス>/');
```

* パーティション(Partition)
    * Hiveはデータを特定基準のディレクトリに分離して保存できるパーティション機能を提供します。
    * テーブルにパーティションを適用したりパーティションを操作したりするには、次のようなクエリが必要です。

``` sql
#テーブルにパーティションを適用して作成
CREATE TABLE default.sample (...) WITH ( partitioned_by = ARRAY['columna', 'columnb'],)
#パーティション照会
SELECT * FROM default"sample$partitions"
#パーティションを操作
system.create_empty_partition(schema_name, table_name, partition_columns, partition_values)
system.sync_partition_metadata(schema_name, table_name, mode, case_sensitive)
```

* 制約事項
    * CSVタイプのテーブルカラムはVARCHARタイプのみサポートされます。
    * DataQueryではObject StorageアクセスのためにS3互換レイヤーを使用し、スキーマまたはテーブルのためのデータパス指定時、s3aプロトコルを使用する必要があります(ex. s3a://example/test)。
    * External tableのexternal\_locationに指定されるデータディレクトリパスオブジェクトが別途存在する必要があります。
        * Object Storageでディレクトリを別途作成した状態で、データが当該ディレクトリにある時のみ正常に連動します。
        * 処理に問題がある場合は、サポートにお問い合わせください。
    * External tableのexternal\_locationパス名にハングルが入っている場合は正常にデータが処理されません。
    * テーブルに接続されたObject Storageバケットが削除されるとテーブルDROPクエリが失敗します。
    * DELETE、UPDATEはパーティションデータに対してのみ制限的に実行できます。
        * [詳細情報](https://trino.io/docs/398/connector/hive.html#data-management)

#### 外部テーブルクエリ利用チュートリアル

1. サンプルCSVファイルを[ダウンロード](https://static.toastoven.net/prod_dataquery/files/facility-boundary-us-all.csv)してObject Storageにアップロードします。

<img src="https://static.toastoven.net/prod_dataquery/dataquery_console_04_en.png"/>

2. Object Storageコンソールでアクセスキー、シークレットキーを発行します。
3. Object Storageのアクセスキー、シークレットキー、エンドポイントを利用してObject Storageデータソースを入力します。
4. クエリエディタに移動し、先ほど追加したObject Storageデータソースを選択し、defaultスキーマを選択します。
5. 次のようにCREATE TABLEクエリを入力して実行します。

``` SQL
CREATE TABLE corona_facility_us
(
    facility_place_id varchar,
    facility_provider_id varchar,
    facility_name varchar,
    facility_latitude varchar,
    facility_longitude varchar,
    facility_country_region varchar,
    facility_country_region_code varchar,
    facility_sub_region_1 varchar,
    facility_sub_region_1_code varchar,
    facility_sub_region_2 varchar,
    facility_sub_region_2_code varchar,
    facility_region_place_id varchar,
    mode_of_transportation varchar,
    travel_time_threshold_minutes varchar,
    facility_catchment_boundary varchar
) 
with (
    format = 'csv',
    external_location = 's3a://csv-test/corona-facility/'
)
```

6. テーブルが正常に追加されたことを確認するためにテーブルを更新します。

<img src="https://static.toastoven.net/prod_dataquery/dataquery_console_05_en.png" width=220/>

7. 該当テーブルで、次のようにクエリを実行します。

``` SQL
SELECT * FROM corona_facility_us
        WHERE facility_place_id = 'ChIJkxHDPsnTQIYR7MH7N-eIdQ0'
          AND facility_latitude = '29.952'
```

8. 合計10件のデータが正常に表示されていることを確認します。

### MySQLデータソースクエリ実行

* MySQLデータソースに対するクエリはTrino-MySQLに基づいて行われます。
* Trino-MySQLは基本的に標準SQL文法に従います。
* MySQLデータソースのスキーマとテーブルは、小文字名に基づいて動作し、表現されます。
* 制約事項
    * UPDATEクエリはサポートしません。
        * [詳細情報](https://trino.io/docs/398/connector/mysql.html#sql-support)
* 外部ツール(JDBC、CLI、BIソリューションなど)と連動できるようにTrinoエンドポイントを提供します。

### Trino cli

* 設定メニューから発行された認証情報、接続情報、TrinoでサポートするCLIツールを利用してコマンドラインからクエリを実行できます。
    * [Trino CLI](https://repo1.maven.org/maven2/io/trino/trino-cli/398/trino-cli-398-executable.jar)

```
# ファイルに実行権限が必要です。chmod +xで付与できます。
# ex) chmod +x trino-cli-398-executable.jar

./trino-cli-398-executable.jar --server <接続URL(必須)> \
  --user <ID(必須)> --password \
  --catalog <データソース名> \
  --schema <スキーマ名>
```

* 設定パラメータ
    * 接続URL(必須)
        * 設定画面で提供された接続URL (ex. [https://x-x-x-x-x.kr1-cluster-dataquery.nhncloudservice.com](https://x-x-x-x-x.kr1-cluster-dataquery.nhncloudservice.com))
    * ID(必須)
        * 認証情報画面で提供されたID
    * パスワード(必須)
        * 認証情報画面で提供されたパスワード
        * コマンドを実行すると表示されるプロンプトウィンドウで入力するか、`export TRINO_PASSWORD=<パスワード>`にあらかじめパスワードを設定しておくことができます。
    * データソース名
        * 接続したデータソース名
    * スキーマ名
        * 接続したデータベース名
* `--debug`オプションを追加してデバッグ情報を追加で出力できます。
* catalog、schema値はコマンドを実行する接続に対する値で、入力しなくてもcli実行することができ、以下のクエリを利用してcatalogやschemaリストを確認できます。
    * show catalogs
    * show schemas
* 詳細は[Trinoガイドページ](https://trino.io/docs/398/client/cli.html)をご覧ください。

### JDBC接続

* **設定**メニューで発行された認証情報、接続情報と、TrinoでサポートするJDBCドライバーを利用してJDBCに接続できます。

```
jdbc:trino://${host}:${port}
jdbc:trino://${host}:${port}/${catalog}
jdbc:trino://${host}:${port}/${catalog}/${schema}
```

* 設定パラメータ
    * host(必須)
        * 設定画面で提供された接続URLで`https://`以外の部分を入力します(ex . x-x-x-x-x.kr1-cluster-dataquery.nhncloudservice.com)。
    * port(必須)
        * 443を入力します。
    * catalog
        * 接続したいデータソース名
    * schema
        * 接続したいスキーマ名
* 接続情報例
    * jdbc:trino://test-dataquery-domain-12345abcd.kr1-cluster-dataquery.nhncloudservice.com:443/catalog/schema
* 詳細は[Trino JDBCガイドページ](https://trino.io/docs/398/client/jdbc.html)をご覧ください。
