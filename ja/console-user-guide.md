## Data & Analytics > DataQuery > コンソール使用ガイド

DataQueryサービスを使用するには、必ずデータソースを追加する必要があります。
以下のような手順でサービスを使用できます。

* 連動するデータソース追加
* データソースを反映するためのクラスタ起動
* Webコンソールのクエリエディタまたは外部接続URLを介した別途ツールでのクエリ実行

## データソース

### データソース追加

* データソース設定および反映制約事項
    * Object Storageタイプのデータソースは最大5個まで登録できます。
    * アクセス制御が設定されたデータソースに接続する場合は、DataQuery IP固定機能を使用する必要があります。
        * DataQuery IP固定機能を使用する場合は、サポートにお問い合わせください。
* **データソースの追加**をクリックします。


### Object Storageデータソースタイプ

* **データソースの追加**をクリックした後、データソースの追加ページでObject Storage情報を入力します。
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
    * 追加設定情報
        * 再帰的パスの読み取り：下位ディレクトリを含むクエリを実行できます。
        * ファイル保存形式：ストレージに保存されるファイルタイプを設定します。ORC、Parquet、CSVなどのタイプをサポートします。        
* その他の事項
    * 連動するObject Storageは、同じNHN Cloudプロジェクト外部に存在できます。
> [注意]
> DataQueryと連動するObject Storageが同じリージョンではない場合、ネットワークトラフィックによる追加料金が発生する可能性があります。

### MySQLデータソースタイプ

* データソース名
        * クエリ実行時に使用されるセパレータで、データソース間で一意の値でなければなりません。
* 接続URL
    * MySQLデータベース接続アドレスです。
    * **jdbc:mysql://[ホスト、ip]:[ポート]?[パラメータ]**フォーマットで入力する必要があります。
    * タイムゾーン処理が必要な場合、serverTimezoneパラメータを設定する必要があります。
        * ex) jdbc:mysql://localhost:10000?**serverTimezone=Asia/Seoul**
* ユーザーID
    * 接続するMySQLアカウント名です。
* パスワード
    * 接続するMySQLパスワードです。

### PostgreSQLデータソースタイプ

* データソース名
    * クエリ実行時に使用される識別子で、データソース間で固有の値でなければなりません。
* 接続URL
    * PostgreSQLデータベース接続アドレスです。
    * **jdbc:postgresql://[ホスト、ip]:[ポート]/[データベース]?[パラメータ]**フォーマットで入力する必要があります。
* ユーザーID
    * 接続するPostgreSQLアカウント名です。
* パスワード
    * 接続するPostgreSQLパスワードです。

### Oracleデータソースタイプ

* データソース名
    * クエリ実行時に使用される識別子で、データソース間で固有の値でなければなりません。
* 接続URL
    * Oracleデータベース接続アドレスです。
    * **jdbc:oracle:thin:@[ホスト、ip]:[ポート]:[SID]** または **jdbc:oracle:thin:@[ホスト、ip]:[ポート]/[SERVICE NAME]** フォーマットで入力する必要があります。
* ユーザーID
    * 接続するOracleアカウント名です。
* パスワード
    * 接続するOracleパスワードです。  
* 追加設定情報
    * 未サポートタイプ処理:サポートしない列データタイプに対する処理方法を設定できます。
    * 基本小数点以下の桁数： 全体の有効桁数(precision)、小数点以下の桁数(scale)設定がない数字の基本小数点桁数を設定します。
    * 数字の切り上げ/切り捨て：Oracle NUMBERデータ型に対する切り上げ/切り捨てポリシーを設定します。

### EDBデータソースタイプ

* データソース名
    * クエリ実行時に使用される識別子で、データソース間で固有の値でなければなりません。
* 接続URL
    * EDBデータベース接続アドレスです。
    * **jdbc:postgresql://[ホスト、ip]:[ポート]?[パラメータ]** フォーマットで入力する必要があります。
* ユーザーID
    * 接続するEDBアカウント名です。
* パスワード
    * 接続するEDBパスワードです。 

### MariaDBデータソースタイプ

* データソース名
    * クエリ実行時に使用される名前で、データソース間で固有の値でなければなりません。
* 接続URL
    * MariaDBデータベース接続アドレスです。
    * **jdbc:mariadb://[ホスト、ip]:[ポート]?[パラメータ]** フォーマットで入力する必要があります。
    * タイムゾーン処理が必要な場合serverTimezoneパラメータを設定する必要があります。
        * ex) jdbc:mariadb://localhost:10000?**serverTimezone=Asia/Seoul**
* ユーザーID
    * 接続するMariaDBアカウント名です。
* パスワード
    * 接続するMariaDBパスワードです。


### Icebergデータソースタイプ

* データソース名
    * クエリ実行時に使用される区切り文字で、データソース間で固有の値でなければなりません。
* アクセスキー、秘密鍵、リージョン
    * 連動するIcebergテーブルデータまたは連動するデータが存在するObject Storageの接続情報です。
    * アクセスキーと秘密鍵はObject Storageコンソールで発行できます。詳細は[Object Storageコンソール使用ガイド](https://docs.toast.com/ko/Storage/Object%20Storage/ko/console-guide/#s3-api)を参照してください。
        * リージョンはObject Storageガイドのリージョン別[S3リージョン](https://docs.toast.com/ko/Storage/Object%20Storage/ko/s3-api-guide/#aws-cli)を参考してください。
    * バケット名
        * システムで基本Icebergテーブル情報を保存するために使用するObject Storageコンテナ名はdataquery-warehouseで、下位パスはicebergです。
        * 連動する既存のデータは他のパスに存在する可能性があります。

> [注意]
> DataQueryと連動するObject Storageが同じリージョンでない場合、ネットワークトラフィックによる追加料金が発生する可能性があります。


## クエリエディタ

* クエリエディタはクラスタ領域、スキーマ領域、保存されたクエリ領域、エディタ領域、結果/コンソール実行領域に区分されます。

<img src="https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_dataquery/dataquery_console_01_en.png"/>

### 1. クラスタ領域

* クラスタのオン/オフを切り替えることができます。
* 追加、変更、削除したデータソース情報を実際の動作に反映させるにはDataQueryクラスタを再起動する必要があります。
* データソースの追加または変更、削除などの動作があった場合、以下のようにクラスタ再起動文言が表示されます。
* クラスタの電源を切るのに1～2分、電源を入れるのに5～7分程度の時間がかかることがあります。
* DataQueryクラスタはすべてのデータソースを反映し、個別のデータソース適用はできません。
* 継続的にクラスタの**オン/オフ**に失敗する場合は、サポートにお問い合わせください。

### 2. スキーマ領域

* 接続設定されたデータソースと、該当ソースで提供する実際のDB 、テーブル、カラム情報を確認できます。
    * information\_schemaはデータソースとの接続情報を持っているDBで、ユーザーが任意にデータを操作できません。
* 各項目の更新アイコンをクリックして、データソース、スキーマ、テーブル、カラム情報を新しく取得できます。
    * ただし、上位スキーマを更新しても下位情報は全部新しく読み込みません。テーブルを更新する場合、テーブルリストのみ新たに取得し、各テーブルのカラム情報はアップデートされません。

### 3. 保存されたクエリ領域

* ユーザーが保存したクエリを管理できます。
* **開く**をクリックすると、現在開いているクエリエディタ領域に保存したクエリを呼び出すことができます。
* **新しいタブを開く**をクリックすると、新しいクエリエディタ領域に保存されたクエリを呼び出すことができます。
* **クエリのコピー**をクリックすると、クリップボードに保存されたクエリをコピーできます。

### 4. エディタ領域

* **\+ クエリ追加**をクリックしてクエリエディタを最大10個まで作成できます。
* **実行**をクリックするか、**ctrl + enter**を入力してクエリを実行でき、エディタ下部で実行中のクエリの進行状態と失敗時の原因ログを確認できます。
* **クエリの保存**をクリックすると、ユーザーがよく使うクエリを保存できます。
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
    * [キーワード、データ型](https://trino.io/docs/462/language.html)
    * [Trinoクエリ](https://trino.io/docs/462/sql.html)
    * [組み込み関数](https://trino.io/docs/462/functions.html)

### 5. 結果/コンソール実行クエリ領域

* クエリエディタで実行されたクエリ結果を確認できます。
    * データサイズに応じて約1MBまたは約5,000個程度の制限された結果を提供します。
    * クエリ結果は最大30MBまでダウンロードできます。
        * Trinoを直接連動(ex. JDBC、CLI)すると、クエリ実行結果全体のデータを取得できます。設定メニューガイドをご覧ください。
        * クエリ結果はクエリ完了時刻から最大7日までダウンロードできます。12月1日13時53分32秒にクエリ実行が完了した場合、12月8日13時53分32秒の前までダウンロードできます。
    * マウス右クリックしてコンソールクエリ結果のコピー、エクスポートを実行できます。
* クエリエディタで実行したクエリリストを提供します。

<img src="https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_dataquery/dataquery_console_02_en.png"/>

* ①クエリ履歴をクリックします。
* ②該当クエリが入力されたクエリウィンドウが追加作成されます。

## クエリ履歴

* 実行したクエリ情報を**クエリ履歴**画面で確認できます。
    * クエリ情報は、クエリ実行後90日間照会可能です。
* 一番右の列の展開ボタンをクリックしてクエリの追加の実行情報を確認できます。**ダウンロード**をクリックしてクエリの全体実行情報をダウンロードできます。
    * ダウンロードファイルにクエリ結果は含まれません。

<img src="https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_dataquery/dataquery_console_03_en.png"/>

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

### クエリ履歴を保存するためのObject Storage連動の無効化案内メール

* クエリ履歴を保存するためのObject Storage認証の有効期限が切れて連動が無効になった場合、通知メールを受け取ることができます。
* 基本受信対象
    * 使用中のDataQueryサービスが有効化されたプロジェクトのDataQuery ADMINロールを持つメンバー

## データソース詳細ガイド

### Object Storageデータソースクエリ実行

* Object Storageデータソースに対するクエリは、Trino-Hiveに基づいて実行されます。
    * Hiveは[Apache Hadoop](https://hive.apache.org/)分散ストレージ環境でSQL作業処理をサポートするためのソリューションです。
* DataQueryではObject StorageアクセスのためにS3互換レイヤーを使用し、スキーマまたはテーブルのためのデータパス指定時、s3aプロトコルを使用する必要があります(ex. s3a://example/test).
* Object Storage上のParquet、JSON、ORC、CSV、Textタイプのデータに対する処理をサポートします。
* Object Storageデータソースはdefaultという名前の基本スキーマを提供し、そのスキーマで作業できます。
> [参考]
> Object Storageクエリに使用するHiveの性能向上が必要な場合は、サポートにお問い合わせください。

#### Hive機能動作のための追加の文法

* Trino-Hiveは基本的に標準SQL文法に従いますが、Hive動作対応のための追加機能/文法が存在します。 [詳細情報](https://trino.io/docs/462/connector/hive.html)
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
system.register_partition(schema_name, table_name, partition_columns, partition_values, location)
```
* パーティション関数
  * sync_partition_metadata
    * オブジェクトのパスからパーティション値を推測して、自動的にパーティション値を登録、削除できます。

      | モード | 説明                                                                              |
      | ----- |-----------------------------------------------------------------------------------|
      | ADD | パーティション値がテーブルに登録されておらず、Object StorageオブジェクトがHiveのパーティションパスに合わせて存在するときに、パーティション値を追加します。 |
      | DROP | パーティション値がすでにテーブルに登録されているが、Object StorageオブジェクトがHiveパーティションパスに存在しない場合は、パーティション値を削除します。 |
      | FULL | ADD, DROPを順番に実行します。                                                            |
    * Object Storageオブジェクトのパスを基準にHiveパーティションの値を推論する方法は次のとおりです。
      * 定義されたexternal\_locationの下にある全てのオブジェクトを照会した後、パスを抽出します。
      * パーティション列がc1列とc2列で指定されている場合、Hiveパーティションとして有効なパスは`/c1=<c1 value>/c2=<c2 value>`を含む必要があります。
      * 例えば、external\_location='s3a://location/tmp/', partitioned_by=ARRAY['year', 'month', 'day']で定義されたテーブルがある場合、 external_locationの下にある全てのオブジェクトのパスを抽出した後、そのパスがs3a://location/tmp/year=yyyy/month=MM/day=dd/のような形式を含む場合、Hiveパーティションパスとして「有効」と判断し、パーティション値を推測します。
    * 注意
      * sync_partition_metadataを実行するには、テーブルで定義したexternal\_locationにコンテナ以下のパスが必ず1つ以上存在する必要があります。例えば、external\_location='s3a://location/tmp/'のように、コンテナがlocationの場合、その下にtmpというパスが1つ以上存在する必要があります。
  * register_partition
    * ユーザーが指定したパスをパーティションの値として直接登録できます。
    * 3番目のパラメータであるpartition_columnsには、Hiveテーブルで定義したパーティション列を入力します。
    * 4番目のパラメータであるpartition_valuesには、登録したいパーティションの値を入力します。
    * 5番目のパラメータであるlocationにオブジェクトが必ず1つ以上存在する必要があります。
* 制約事項
    * CSVタイプのテーブルカラムはVARCHARタイプのみサポートされます。
    * DataQueryではObject StorageアクセスのためにS3互換レイヤーを使用し、スキーマまたはテーブルのためのデータパス指定時、s3aプロトコルを使用する必要があります(ex. s3a://example/test)。
    * External tableのexternal\_locationに指定されるデータディレクトリパスオブジェクトが別途存在する必要があります。
        * Object Storageでディレクトリを別途作成した状態で、データが当該ディレクトリにある時のみ正常に連動します。
        * 処理に問題がある場合は、サポートにお問い合わせください。
    * External tableのexternal\_locationパス名にハングルが入っている場合は正常にデータが処理されません。
    * テーブルに接続されたObject Storageバケットが削除されるとテーブルDROPクエリが失敗します。
    * DELETE、UPDATEはパーティションデータに対してのみ制限的に実行できます。
        * [詳細情報](https://trino.io/docs/462/connector/hive.html#data-management)

#### 外部テーブルクエリ利用チュートリアル

1. サンプルCSVファイルを[ダウンロード](https://static.toastoven.net/prod_dataquery/files/facility-boundary-us-all.csv)してObject Storageにアップロードします。

<img src="https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_dataquery/dataquery_console_04_en.png"/>

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

<img src="https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_dataquery/dataquery_console_05_en.png" width=220/>

7. 該当テーブルで、次のようにクエリを実行します。

``` SQL
SELECT * FROM corona_facility_us
        WHERE facility_place_id = 'ChIJkxHDPsnTQIYR7MH7N-eIdQ0'
          AND facility_latitude = '29.952'
```

8. 合計10件のデータが正常に表示されていることを確認します。

### MySQLデータソースクエリ実行

* MySQLデータソースに対するクエリはTrino-MySQLに基づいて行われます。
* MySQLデータソースのスキーマとテーブルは、小文字名に基づいて動作し、表現されます。
* 同じ名前で大文字/小文字が異なるテーブルがある場合、クエリ実行とスキーマ収集が正常に動作しない場合があります。
* 制約事項
    * DELETEは特定の条件が満たされた場合のみ制限的に実行できます。
        * where句が存在する時、術語(Predicate)がデータソースに完全にプッシュダウン(Pushdown)できる必要があります。
        * テキストタイプの列はプッシュダウンがサポートされません。
        * [詳細情報](https://trino.io/docs/462/connector/mysql.html#predicate-pushdown-support)
    * UPDATEは、特定の条件が満たされる場合のみ制限的に実行できます。
        * 定数値への割り当てと術語(Predicate)が存在する場合のみ実行することができます。
        * 算術式、関数呼び出しおよび定数以外の値へのUPDATE文はサポートされません。
        * テーブルのすべての列を同時に更新することはできません。
        * [詳細情報](https://trino.io/docs/462/connector/mysql.html#update)

### PostgreSQLデータソースクエリの実行

* PostgreSQLデータソースに対するクエリは、Trino-PostgreSQLに基づいて実行されます。
* PostgreSQLデータソースのスキーマとテーブルは小文字の名前に基づいて動作し、表現されます。
* 大文字と小文字が異なる同じ名前のテーブルがある場合、クエリの実行とスキーマの収集が正常に動作しない場合があります。
* 制約事項
    * DELETEは特定の条件が満たされた場合のみ制限的に実行できます。
        * where句が存在する時、術語(Predicate)がデータソースに完全にプッシュダウン(Pushdown)できる必要があります。
        * CHAR または VARCHAR のような文字列タイプに対する範囲条件(>, < または BETWEEN)はプッシュダウンがサポートされません。
        * テキストタイプに対する等価比較条件(IN, =, !=)はプッシュダウンがサポートされます。
        * [詳細情報](https://trino.io/docs/462/connector/postgresql.html#predicate-pushdown-support)
    * UPDATEは、特定の条件が満たされる場合のみ制限的に実行できます。
        * 定数値への割り当てと術語(Predicate)が存在する場合のみ実行することができます。
        * 算術式、関数呼び出しおよび定数以外の値へのUPDATE文はサポートされません。
        * テーブルのすべての列を同時に更新することはできません。
        * [詳細情報](https://trino.io/docs/462/connector/postgresql.html#update)

### Oracleデータソースクエリの実行

* Oracleデータソースに対するクエリは、Trino-Oracleに基づいて実行されます。
* Oracleデータソースのスキーマとテーブルは、小文字の名前に基づいて動作し、表現されます。
* 大文字と小文字が異なる同じ名前のテーブルがある場合、クエリの実行とスキーマの収集が正常に動作しない場合があります。
* 制約事項
    * DELETE, UPDATEは特定の条件が満たされる場合のみ制限的に実行できます。
        * where句が存在する時、術語(Predicate)がデータソースに完全にプッシュダウン(Pushdown)できる必要があります。
        * CLOB, NCLOB, BLOB, or RAW(n)であるOracleタイプの列はプッシュダウンがサポートされません。
        * [詳細情報](https://trino.io/docs/462/connector/oracle.html#predicate-pushdown-support)
    * UPDATEは、特定の条件が満たされる場合のみ制限的に実行できます。
        * 定数値への割り当てと術語(Predicate)が存在する場合のみ実行することができます。
        * 算術式、関数呼び出しおよび定数以外の値へのUPDATE文はサポートされません。
        * テーブルのすべての列を同時に更新することはできません。
        * [詳細情報](https://trino.io/docs/462/connector/oracle.html#update)

### EDBデータソースクエリの実行

* EDBデータソースに対するクエリは、Trino-PostgreSQLに基づいて実行されます。
* EDBデータソースのスキーマとテーブルは小文字の名前に基づいて動作し、表現されます。
* 大文字と小文字が異なる同じ名前のテーブルがある場合、クエリの実行とスキーマの収集が正常に動作しない場合があります。
* 制約事項
    * DELETEは特定の条件が満たされた場合のみ制限的に実行できます。
        * where句が存在する時、術語(Predicate)がデータソースに完全にプッシュダウン(Pushdown)できる必要があります。
        * CHAR または VARCHAR のような文字列タイプに対する範囲条件(>, < または BETWEEN)はプッシュダウンがサポートされません。
        * テキストタイプに対する等価比較条件(IN, =, !=)はプッシュダウンがサポートされます。
        * [詳細情報](https://trino.io/docs/462/connector/postgresql.html#predicate-pushdown-support)
    * UPDATEは、特定の条件が満たされる場合のみ制限的に実行できます。
        * 定数値への割り当てと術語(Predicate)が存在する場合のみ実行することができます。
        * 算術式、関数呼び出しおよび定数以外の値へのUPDATE文はサポートされません。
        * テーブルのすべての列を同時に更新することはできません。
        * [詳細情報](https://trino.io/docs/462/connector/postgresql.html#update)

### MariaDBデータソースクエリ実行

* MariaDBデータソースに対するクエリはTrino-MariaDBに基づいて実行されます。
* MariaDBデータソースのスキーマとテーブルは小文字の名前に基づいて動作し、表現されます。
* 大文字と小文字が異なる同じ名前のテーブルがある場合、クエリの実行とスキーマの収集が正常に動作しない場合があります。
* 制約事項
    * DELETEは特定の条件が満たされた場合のみ制限的に実行できます。
        * where節が存在する場合、Predicateがデータソースに完全にプッシュダウン(Pushdown)できる必要があります。
        * テキストタイプの列はプッシュダウンがサポートされません。
        * [詳細情報](https://trino.io/docs/462/connector/mariadb.html#predicate-pushdown-support)
    * UPDATEは、特定の条件が満たされた場合のみ制限的に実行できます。
        * 定数値への割り当てとPredicateが存在する場合のみ実行できます。
        * 算術式、関数呼び出しおよび定数以外の値へのUPDATE文はサポートされません。
        * テーブルのすべての列を同時に更新することはできません。
        * [詳細情報](https://trino.io/docs/462/connector/mariadb.html#update)


### Icebergデータソースクエリ実行

* Icebergデータソースに対するクエリは、Trino-Icebergに基づいて実行されます。
* Object Storageに存在するIcebergテーブルデータ及びサポートするフォーマットのデータに対して連動できます。
    * PARQUET(基本フォーマット), ORC, AVROタイプのデータをサポートします。
* Object StorageへのアクセスにS3互換レイヤーを使用し、スキーマまたはテーブルのデータパス指定時にs3aプロトコルを使用する必要があります(例：s3a://example/test)。

#### スキーマ

* CREATE SCHEMA文で作成できます。

```sql
# 基本パスにスキーマ作成
CREATE SCHEMA example_schema;
# 指定パスにスキーマ作成
CREATE SCHEMA example_schema
WITH (location = 's3a://my-bucket/example_schema/');
```

#### テーブル

* CREATE TABLEまたはCREATE TABLE AS文で作成できます。
* テーブルプロパティ指定でテーブルのメタデータを設定できます。
    * テーブルプロパティはWITH節を使用して指定できます。

```sql
CREATE TABLE example_table (c1 INTEGER, c2 DATE, c3 DOUBLE);
## プロパティ指定
CREATE TABLE example_table (c1 INTEGER, c2 DATE, c3 DOUBLE)
WITH (
    format = 'PARQUET',
    partitioning = ARRAY['c1', 'c2'],
    sorted_by = ARRAY['c3'],
    location = 's3a://my-bucket/example_schema/example_table/'
);
```

* テーブルプロパティ
    * テーブルのメタデータを設定できます。 [追加情報](https://trino.io/docs/462/connector/iceberg.html#table-properties)

| プロパティ名 | 説明 |
| ----- | --- |
| format | テーブルデータファイルの形式を指定します。 PARQUET, ORC、またはAVRO. <br> デフォルト値はPARQUETです。 |
| partitioning | テーブルパーティションを指定します。テーブルがc1列とc2列に分割されている場合、partitioning=ARRAY['c1', 'c2']で指定できます。 |
| sorted\_by | 個別データファイルを保存する際、指定した列の値でソートして保存します。 |
| location | テーブルのObject Storageパスを指定します。<br>プロパティを設定しない場合、デフォルトのパスより下のスキーマパスに保存されます。 |

#### パーティション

* テーブルプロパティを使用して、テーブルデータが分割保存された構造の分割された(パーティションされた)テーブルを作成できます。
    * パーティション列がc1列とc2列に指定されている場合、該当パーティションのデータはテーブルデータパス下位の`/c1=<c1値>/c2=<c2値>`に保存されます。
* Icebergは書き込み(write)されたデータの値を通じてパーティションを自動的に管理してくれるので、パーティションを手動で追加/管理できません。
* テーブル列を利用(変換)してパーティションを指定できる機能をサポートします。
    * year, month, day, hour, bucket, truncate [追加情報](https://trino.io/docs/462/connector/iceberg.html#partitioned-tables)

| 変換 | サポートタイプ | 説明 |
| --- | ----- | --- |
| year(ts) | DATE, TIMESTAMP | 年度別 |
| month(ts) | DATE, TIMESTAMP | 月別 |
| day(ts) | DATE, TIMESTAMP | 日別 |
| hour(ts) | TIMESTAMP | 時間別 |

#### メタデータテーブル

* メタデータテーブルを照会してIcebergテーブルのメタ情報を確認できます。 [追加情報](https://trino.io/docs/462/connector/iceberg.html#metadata-tables)
    * $properties
        * テーブルプロパティ
    * $history
        * テーブルのメタデータが変更された履歴
    * $snapshots
        * データに変化が発生したときに記録されたテーブル形状履歴
    * $manifests
        * データファイルの集合を管理するファイルの情報
    * $partitions
        * テーブルの詳細なパーティション情報
    * $files
        * 現在のテーブルのスナップショット

```sql
## テーブルプロパティ照会
SELECT * FROM "test_table$properties"
```

#### データ管理

* テーブル登録
    * すでにファイルとして存在するIcebergテーブルが存在するが、登録されていないIcebergテーブルを登録する方法です。
    * register\_tableを呼び出して登録できます。

```sql
CALL example.system.register_table(schema_name => 'example_schema', table_name => 'example_table', table_location => 's3a://my-bucket/example_schema/example_table')
```

* テーブル削除
    * DROP TABLE文でテーブルを削除できます。このコマンドは、実際のIcebergデータを削除します。
* テーブル除外
    * テーブルを削除(DROP)せず、テーブルリストから除外する時に使用できます。

```sql
CALL example.system.unregister_table(schema_name => 'example_schema', table_name => 'example_table')
```

* スキーマ進化(schema evolution)
    * Icebergはメタデータだけを変更するスキーマ進化をサポートします。スキーマアップデートを実行する際、データファイル自体は変更されません。
    * 列の追加、削除、再ソート、名前変更、タイプ変更をサポートします。
    * タイプ変更は既存タイプから拡張されるタイプの変更のみをサポートします。
        * INTEGERからBIGINT
        * REALからDOUBLE
        * DECIMALの精度向上
* スナップショット整理
    * 書き込み、変更、圧縮などで作成されたスナップショットを整理します。
    * 不要になった情報とデータファイルを除去してメタデータのサイズを維持できます。
    * テーブルメタデータのサイズを小さく維持するにはスナップショットを定期的に整理することを推奨します。

```sql
ALTER TABLE test_table EXECUTE expire_snapshots(retention_threshold => '7d')
```

* 孤立したファイルの整理
    * 現在存在するメタデータと関連がなくなったデータファイルを削除します。
        * 該当ファイルのうち、指定時間以前に作成された対象を削除します。
    * テーブルのデータディレクトリサイズを管理するにはファイルを整理することを推奨します。

```sql
ALTER TABLE test_table EXECUTE remove_orphan_files(retention_threshold => '7d')
```

#### Icebergタイプマッピング情報

* IcebergタイプはDataQueryで処理できるタイプで、下記のようにマッピングされます。

| DataQueryタイプ | Icebergタイプ |
| ----------- | --------- |
| BOOLEAN | BOOLEAN |
| INTEGER | INT |
| BIGINT | LONG |
| REAL | FLOAT |
| DOUBLE | DOUBLE |
| DECIMAL(p,s) | DECIMAL(p,s) |
| DATE | DATE |
| TIME(6) | TIME |
| TIMESTAMP(6) | TIMESTAMP |
| TIMESTAMP(6) WITH TIME ZONE | TIMESTAMPTZ |
| VARCHAR | STRING |
| UUID | UUID |
| VARBINARY | BINARY |
| ROW(...) | STRUCT(...) |
| ARRAY(e) | LIST(e) |
| MAP(k,v) | MAP(k,v) |
#### Object Storageに存在するParquetファイルをIcebergテーブルに追加
* 特定のファイルまたは特定のパスの下のファイルをIcebergテーブルにデータとして追加できます。
* パーティションがないテーブルはadd_files、パーティションが定義されたテーブルはadd_files_with_partitionでデータファイルとパーティション値を追加できます。
* add_files関数

  |引数 | サポートする値                  | 説明                                                                                                                                                                                   |
  | --- |---------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | location | データファイルパス               | 追加したいデータファイルのパス                                                                                                                                                                      |
  | format | PARQUET(基本フォーマット), ORC, AVRO | 追加したいデータファイルのフォーマット                                                                                                                                                                      |
  | recursive_directory | FAIL(デフォルト値), TRUE, FALSE   | location以下のパスを再帰的に探索できる場合の動作<br>FAIL => 入力したデータファイルパスが2段階の深さまで再帰的に探索できる場合、クエリに失敗します。<br> TRUE => 入力したデータファイルパスより下を全て再帰的に探索します。<br>FALSE => 入力したデータファイルパス2段階の深さから無視します。 |
  |duplicate_file  | FAIL(デフォルト値), SKIP, ADD     | 登録しようとするデータファイルが既に登録されたicebergテーブルのデータファイルと重複している場合の動作<br>FAIL => icebergテーブルに既に登録されたデータファイルと比較して重複したデータファイルがある場合、クエリに失敗します。<br>SKIP => 重複したファイルは無視します。<br>ADD => データファイルを追加します。           |
```sql
## example_tableにmybucket/a/path下位データファイルを追加
ALTER TABLE example.system.example_table 
EXECUTE add_files(location => 's3://my-bucket/a/path', format => 'PARQUET', recursive_directory => 'FAIL', duplicate_file => 'FAIL')
```
* add_files_with_partition関数
  * パーティション変形を定義したテーブルもサポートします。
  * 登録するパーティション列タイプがDATEの場合は`YYYY-MM-DD`, TIMESTAMPの場合は`YYYY-MM-DD HH:mm:ss`の形式で入力する必要があります。 timezoneがあるTIMESTAMPの場合は`YYYY-MM-DD HH:mm:ss Asia/Seoul`のように最後にzoneIdを指定する必要があります。

    |引数 | サポートする値                  | 説明                                                                                                                                                                                    |
    | --- |---------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | location | データファイルパス               | 追加したいデータファイルのパス                                                                                                                                                                       |
    |partition_columns| ARRAY['partition_column'] | icebergテーブルに定義されたパーティション列を羅列し、テーブルがc1, c2列に分割されている場合はARRAY['c1', 'c2']と入力                                                                                                               |
    |partition_values| ARRAY['partition_value']  | 登録したいパーティション値                                                                                                                                                                           |
    | format | PARQUET(基本フォーマット), ORC, AVRO | 追加するデータファイルのフォーマット                                                                                                                                                                      |
    | recursive_directory | FAIL(デフォルト値), TRUE, FALSE | location以下のパスを再帰的に探索できる場合の動作<br>FAIL => 入力したデータファイルのパスが2段階の深さまで再帰的に探索できる場合、クエリを失敗させます<br> TRUE => 入力したデータファイルのパスより下を再帰的に探索します<br>FALSE => 入力したデータファイルのパス2段階の深さから無視します。 |
    |duplicate_file  | FAIL(デフォルト値), SKIP, ADD     | 登録しようとするデータファイルが既に登録されたicebergテーブルのデータファイルと重複している場合の動作<br>FAIL => icebergテーブルに既に登録されたデータファイルと比較して重複したデータファイルがある場合、クエリに失敗します<br>SKIP => 重複したファイルは無視します<br>ADD => データファイルを追加します。            |
```sql
## パーティション列がyearであり、day変換が適用されたicebergテーブル
ALTER TABLE example.system.example_table 
EXECUTE add_files_with_partition(location => 's3://my-bucket/a/path', partition_columns => ARRAY['year'], partition_values => ARRAY['2024-11-21'], format => 'PARQUET', recursive_directory => 'TRUE', duplicate_file => 'FAIL')
```
#### 注意及び制約事項

* 同じパスにIcebergテーブルを重複して作成することはできません。
* 列を変換してパーティションを構成する際、同じ列を使用することはできません。
    * 例：1つのDATEタイプを持つ列でyear, month 2つのパーティションを設定できません。

#### FAQ

* 既にObject StorageにIcebergデータが存在します。どのようにDataQueryに適用できますか？
    * register_tableを実行して登録できます。データ管理 > テーブル登録をご確認ください。
* Object StorageにはParquetファイルのみ存在します。どのようにIcebergテーブルにすることができますか？
    * Icebergテーブルを作成した後、add_files、add_files_with_partition関数を使用してデータを追加できます。
* すでに存在するIcebergテーブルにParquetデータだけ追加したいです。
    * Icebergテーブルを作成した後、add_files、add_files_with_partition関数を使用してデータを追加できます。

## 外部連動
### Trino cli

* 設定メニューから発行された認証情報、接続情報、TrinoでサポートするCLIツールを利用してコマンドラインからクエリを実行できます。
  * DataQueryは現在Trino 455バージョンを基盤にサービスしています。
  * [Trino CLI](https://repo1.maven.org/maven2/io/trino/trino-cli/455/trino-cli-455-executable.jar)

```
# ファイルに実行権限が必要です。chmod +xで付与できます。
# 例) chmod +x trino-cli-455-executable.jar

./trino-cli-455-executable.jar --server <接続URL(必須)> \
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
* 詳細は[Trinoガイドページ](https://trino.io/docs/462/client/cli.html)をご覧ください。

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
* 詳細は[Trino JDBCガイドページ](https://trino.io/docs/462/client/jdbc.html)をご覧ください。
