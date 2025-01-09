## Data & Analytics > DataQuery > 콘솔 사용 가이드

DataQuery 서비스를 사용하려면 반드시 데이터 소스를 추가해야 합니다.
아래와 같은 절차를 통해 서비스를 사용할 수 있습니다.

* 연동할 데이터 소스 추가
* 데이터 소스를 반영하기 위한 클러스터 시작
* 웹 콘솔의 쿼리 편집기 또는 외부 접속 URL을 통한 별도 툴에서의 쿼리 실행

## 데이터 소스

### 데이터 소스 추가

* 데이터 소스 설정 및 반영 제약 사항
    * Object Storage 유형의 데이터 소스는 최대 5개까지 등록할 수 있습니다.
    * 접근 제어가 설정된 데이터 소스 연결 시에는 DataQuery IP 고정 기능을 사용해야 합니다.
        * DataQuery IP 고정 기능을 사용하려면 고객 센터로 문의하십시오.
* **데이터 소스 추가**를 클릭합니다.


### Object Storage 데이터 소스 유형

* **데이터 소스 추가**를 클릭한 뒤 데이터 소스 추가 페이지에서 Object Storage 정보를 입력합니다.
    * 데이터 소스 이름
        * 쿼리 수행 시 사용되는 구분자이며, 데이터 소스 사이에서 고유한 값이어야 합니다.
    * 액세스 키, 비밀 키, 리전
        * 연동할 데이터가 존재하는 Object Storage의 연결 정보입니다.
        * 액세스 키와 비밀 키는 Object Storage 콘솔에서 발급할 수 있습니다. 자세한 내용은 [Object Storage 콘솔 사용 가이드](https://docs.toast.com/ko/Storage/Object%20Storage/ko/console-guide/#s3-api)를 참고하십시오.
        * 리전은 Object Storage 가이드의 리전별 [S3 리전](https://docs.toast.com/ko/Storage/Object%20Storage/ko/s3-api-guide/#aws-cli)을 참고하십시오.
    * 버킷 이름
        * 시스템에서 기본 테이블 정보나 관리 테이블 정보, 데이터를 저장하기 위해 사용하는 Object Storage 컨테이너명(dataquery-warehouse)입니다.
            * 자체적으로 dataquery-warehouse 컨테이너를 생성해 사용합니다.
        * 연동할 기존 데이터들은 dataquery-warehouse 컨테이너 외부에 존재할 수 있습니다.
    * 추가 설정 정보
        * 재귀적 경로 읽기: 하위 디렉터리를 포함한 쿼리를 실행할 수 있습니다.
        * 파일 저장 형식: 스토리지에 저장될 파일 타입을 설정합니다. ORC, Parquet, CSV 등의 타입을 지원합니다.
* 그 외 사항
    * 연동할 Object Storage는 같은 NHN Cloud 프로젝트 외부에 존재할 수 있습니다.
> [주의]
> DataQuery와 연동할 Object Storage가 서로 동일한 리전이 아닐 경우 네트워크 트래픽으로 인한 추가 요금이 발생할 수 있습니다.

### MySQL 데이터 소스 유형

* 데이터 소스 이름
    * 쿼리 수행 시 사용되는 구분자이며, 데이터 소스 사이에서 고유한 값이어야 합니다.
* 접속 URL
    * MySQL 데이터베이스 접속 주소입니다.
    * **jdbc:mysql://[호스트,ip]:[포트]?[파라미터]** 포맷으로 입력해야 합니다.
    * 타임존 처리가 필요할 경우 serverTimezone 파라미터를 설정해야 합니다.
        * ex) jdbc:mysql://localhost:10000?**serverTimezone=Asia/Seoul**
* 사용자 ID
    * 접속할 MySQL 계정명입니다.
* 비밀번호
    * 접속할 MySQL 비밀번호입니다.

### PostgreSQL 데이터 소스 유형

* 데이터 소스 이름
    * 쿼리 수행 시 사용되는 구분자이며, 데이터 소스 사이에서 고유한 값이어야 합니다.
* 접속 URL
    * PostgreSQL 데이터베이스 접속 주소입니다.
    * **jdbc:postgresql://[호스트,ip]:[포트]/[데이터베이스]?[파라미터]** 포맷으로 입력해야 합니다.
* 사용자 ID
    * 접속할 PostgreSQL 계정명입니다.
* 비밀번호
    * 접속할 PostgreSQL 비밀번호입니다.

### Oracle 데이터 소스 유형

* 데이터 소스 이름
    * 쿼리 수행 시 사용되는 구분자이며, 데이터 소스 사이에서 고유한 값이어야 합니다.
* 접속 URL
    * Oracle 데이터베이스 접속 주소입니다.
    * **jdbc:oracle:thin:@[호스트,ip]:[포트]:[SID]** 또는 **jdbc:oracle:thin:@[호스트,ip]:[포트]/[SERVICE NAME]** 포맷으로 입력해야 합니다.
* 사용자 ID
    * 접속할 Oracle 계정명입니다.
* 비밀번호
    * 접속할 Oracle 비밀번호입니다.  
* 추가 설정 정보
    * 미지원 타입 처리: 지원하지 않는 열 데이터 타입에 대한 처리 방법을 정할 수 있습니다.
    * 기본 소수부 자릿수: 전체 유효 자릿수(precision), 소수점 이하 자릿수(scale) 설정이 없는 숫자에 대한 기본 소수부 자릿수를 설정합니다.
    * 숫자 올림/버림: Oracle NUMBER 데이터 타입에 대한 올림/버림 정책을 설정합니다.

### EDB 데이터 소스 유형

* 데이터 소스 이름
    * 쿼리 수행 시 사용되는 구분자이며, 데이터 소스 사이에서 고유한 값이어야 합니다.
* 접속 URL
    * EDB 데이터베이스 접속 주소입니다.
    * **jdbc:postgresql://[호스트,ip]:[포트]?[파라미터]** 포맷으로 입력해야 합니다.
* 사용자 ID
    * 접속할 EDB 계정명입니다.
* 비밀번호
    * 접속할 EDB 비밀번호입니다.  

### MariaDB 데이터 소스 유형

* 데이터 소스 이름
    * 쿼리 수행 시 사용되는 구분자이며, 데이터 소스 사이에서 고유한 값이어야 합니다.
* 접속 URL
    * MariaDB 데이터베이스 접속 주소입니다.
    * **jdbc:mariadb://[호스트,ip]:[포트]?[파라미터]** 포맷으로 입력해야 합니다.
    * 타임존 처리가 필요할 경우 serverTimezone 파라미터를 설정해야 합니다.
        * ex) jdbc:mariadb://localhost:10000?**serverTimezone=Asia/Seoul**
* 사용자 ID
    * 접속할 MariaDB 계정명입니다.
* 비밀번호
    * 접속할 MariaDB 비밀번호입니다.


### Iceberg 데이터 소스 유형

* 데이터 소스 이름
    * 쿼리 수행 시 사용되는 구분자이며, 데이터 소스 사이에서 고유한 값이어야 합니다.
* 액세스 키, 비밀 키, 리전
    * 연동할 Iceberg 테이블 데이터 또는 연동할 데이터가 존재하는 Object Storage의 연결 정보입니다.
    * 액세스 키와 비밀 키는 Object Storage 콘솔에서 발급할 수 있습니다. 자세한 내용은 [Object Storage 콘솔 사용 가이드](https://docs.toast.com/ko/Storage/Object%20Storage/ko/console-guide/#s3-api)를 참고하세요.
        * 리전은 Object Storage 가이드의 리전별 [S3 리전](https://docs.toast.com/ko/Storage/Object%20Storage/ko/s3-api-guide/#aws-cli)을 참고하세요.
    * 버킷 이름
        * 시스템에서 기본 Iceberg 테이블 정보를 저장하기 위해 사용하는 Object Storage 컨테이너명은 dataquery-warehouse이고 하위 경로는 iceberg입니다.
        * 연동할 기존 데이터들은 다른 경로에 존재할 수도 있습니다.

> [주의]
> DataQuery와 연동할 Object Storage가 서로 동일한 리전이 아닐 경우 네트워크 트래픽으로 인한 추가 요금이 발생할 수 있습니다.


## 쿼리 편집기

* 쿼리 편집기는 클러스터 영역, 스키마 영역, 저장된 쿼리 영역, 편집기 영역, 결과/콘솔 실행 영역으로 구분됩니다.

<img src="https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_dataquery/dataquery_console_01_ko.png"/>

### 1. 클러스터 영역

* 클러스터를 켜거나 끌 수 있습니다.
* 추가, 변경, 삭제한 데이터 소스 정보가 실제 동작에 반영되려면 DataQuery 클러스터를 다시 시작해야 합니다.
* 데이터 소스를 추가했거나 변경, 삭제 등의 동작이 있었을 경우 아래와 같이 클러스터 재시작 문구가 나타납니다.
* 클러스터를 끄는 데 1~2분, 켜는 데 5~7분 정도의 시간이 소요될 수 있습니다.
* DataQuery 클러스터는 모든 데이터 소스를 반영하며, 개별적인 데이터 소스 적용은 불가능합니다.
* 지속적으로 클러스터 **켜기** 또는 **끄기**에 실패할 경우, 고객 센터로 문의하십시오.

### 2. 스키마 영역

* 연결 설정된 데이터 소스와 해당 소스에서 제공하는 실제 DB , 테이블, 칼럼 정보를 확인할 수 있습니다.
    * information\_schema는 데이터 소스와의 연결 정보를 가지고 있는 DB로 사용자가 임의로 데이터를 조작할 수 없습니다.
* 각 항목의 새로 고침 아이콘을 클릭해 데이터 소스, 스키마, 테이블, 칼럼 정보를 새롭게 가져올 수 있습니다.
    * 단, 상위 스키마를 새로 고침하더라도 하위 정보는 새로 불러오지 않습니다. 테이블을 새로 고침할 경우 테이블 목록만 새로 가져오고 각 테이블의 칼럼 정보는 업데이트되지 않습니다.

### 3. 저장된 쿼리 영역

* 사용자가 저장한 쿼리를 관리할 수 있습니다.
* **열기**를 클릭해 현재 열려 있는 쿼리 편집기 영역에 저장한 쿼리를 불러올 수 있습니다.
* **새 탭 열기**를 클릭해 새로운 쿼리 편집기 영역에 저장된 쿼리를 불러올 수 있습니다.
* **쿼리 복사**를 클릭해 클립보드에 저장된 쿼리를 복사할 수 있습니다.

### 4. 편집기 영역

* **\+ 쿼리 추가**를 클릭해 쿼리 편집기를 최대 10개까지 생성할 수 있습니다.
* **실행**을 클릭하거나 **ctrl + enter**를 입력하여 쿼리를 실행할 수 있으며, 편집기 하단에서 실행 중인 쿼리의 진행 상태와 실패 시 원인 로그를 확인할 수 있습니다.
* **쿼리 저장**을 클릭해 사용자가 자주 사용하는 쿼리를 저장할 수 있습니다.
* 쿼리 작성 시 수집된 데이터 소스, 스키마, 테이블, 칼럼명에 대한 자동 완성을 지원합니다.

#### SQL 가이드

* DataQuery의 SQL은 Trino 기준에 따라 동작합니다.
    * Trino는 표준 SQL 문법(ANSI SQL)을 따릅니다.
    * Trino는 자체적으로 데이터를 가지지 않으며, 여러 데이터 소스들과의 연동을 통해 데이터를 처리합니다.
        * 데이터 소스별로 예외적인 문법이나 제약 사항이 존재할 수 있습니다.
    * 트랜잭션 처리(OLTP) 작업이 아닌 분석 처리(OLAP) 작업에 맞춰 설계되었습니다.
* 데이터 타입
    * BOOLEAN, 정수형, 소수점, 문자열, 날짜, UUID, 하이퍼로그 등의 타입을 지원합니다.
* Trino 쿼리
    * DDL(Data Definition Language, 데이터 정의어), DML(Data Manipulation Language, 데이터 조작어)을 지원하며 아래와 같은 추가 구문을 지원합니다.
        * 메타데이터를 확인할 수 있는 구문: SHOW CATALOGS, SHOW SCHEMAS, SHOW TABLES, SHOW STATS FOR
        * 시스템의 내장 프로시저(Procedure)를 확인하거나 쿼리의 실행 계획을 확인할 수 있는 구문: CALL, EXPLAIN
* 자세한 사항은 Trino의 가이드 문서를 참고하십시오.
    * [키워드, 데이터 타입](https://trino.io/docs/462/language.html)
    * [Trino 쿼리](https://trino.io/docs/462/sql.html)
    * [내장 함수](https://trino.io/docs/462/functions.html)

### 5. 결과/콘솔 실행 쿼리 영역

* 쿼리 편집기에서 실행된 쿼리 결과를 확인할 수 있습니다.
    * 데이터 크기에 따라 약 1MB 또는 약 5,000개 정도의 제한된 결과를 제공합니다.
    * 쿼리 결과는 최대 30MB까지 다운로드할 수 있습니다.
        * Trino를 직접 연동(ex. JDBC, CLI)하면 쿼리 수행 결과 전체에 대한 데이터를 얻을 수 있습니다. 설정 메뉴 가이드를 참고하십시오.
        * 쿼리 결과는 쿼리 완료 시각으로부터 최대 7일까지 다운로드할 수 있습니다. 12월 1일 13시 53분 32초에 쿼리 실행이 완료될 경우 12월 8일 13시 53분 32초 전까지 다운로드할 수 있습니다.
    * 마우스 오른쪽 버튼을 클릭하여 콘솔 쿼리 결과 복사, 내보내기를 실행할 수 있습니다.
* 쿼리 편집기에서 실행한 쿼리 목록을 제공합니다.

<img src="https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_dataquery/dataquery_console_02_ko.png"/>

* ① 쿼리 이력을 클릭합니다.
* ② 해당 쿼리가 입력된 쿼리 창이 추가 생성됩니다.

## 쿼리 이력

* 실행한 쿼리 정보를 **쿼리 이력** 화면에서 확인할 수 있습니다.
    * 쿼리 정보는 쿼리 실행 이후 90일간 조회 가능합니다.
* 가장 오른쪽 열의 펼침 버튼을 클릭해 쿼리의 추가적인 실행 정보를 확인할 수 있으며, **다운로드**를 클릭해 쿼리의 전체 실행 정보를 내려받을 수 있습니다.
    * 다운로드 파일에 쿼리 결과는 포함되지 않습니다.

<img src="https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_dataquery/dataquery_console_03_ko.png"/>

## 설정

### 클러스터 설정
* 클러스터에 설정된 인스턴스 유형과 노드 수를 확인할 수 있습니다.
    * 유형에 대한 설명이나 설정에서 제공되는 목록 이외의 유형은 [서비스별 요금](https://www.nhncloud.com/kr/pricing/by-service?c=Data%20%26%20Analytics&s=DataQuery)에서 확인할 수 있습니다.
* 인스턴스 유형과 워커 수를 변경할 수 있습니다.
    * 워커 수는 최소 1개에서 최대 5개까지 설정할 수 있습니다.
    * 설정은 클러스터가 꺼진 상태(OFF)에서만 수정이 가능합니다.

### 외부 연동
* 외부 툴(JDBC, CLI, BI 솔루션 등)과 연동할 수 있도록 Trino 엔드포인트를 제공하며 **설정** 페이지에서 제공하는 정보를 이용하여 연동할 수 있습니다.
* 엔드포인트 접속을 위해서는 개인별 인증 정보가 필요하며, **설정** 메뉴에서 **인증 키** 발급을 클릭해 발급 받을 수 있습니다.
    * 개인별 인증 정보는 ID와 인증 키로 구성되어 있으며 엔드포인트에 접속할 때 사용자 이름(ID)과 비밀번호(인증 키)로 활용됩니다.
    * 비밀번호(인증 키)는 최초 발급 시에만 확인할 수 있습니다. 인증 키를 분실할 경우 **인증 키 재발급**을 클릭해 새 인증 키를 발급 받아야 합니다.
    * 발급/재발급된 인증 키는 발급하고 5분이 지난 뒤부터 사용할 수 있습니다.
* 인증 정보가 발급되었다면 Trino 엔드포인트 접속 정보가 화면 하단에 활성화됩니다.

### 쿼리 이력 저장을 위한 Object Storage 연동 비활성화 안내 이메일

* 쿼리 이력 저장을 위한 Object Storage 인증이 만료되어 연동이 비활성화되었을 때 알림 메일을 수신할 수 있습니다.
* 기본 수신 대상
    * 사용 중인 DataQuery 서비스가 활성화된 프로젝트의 DataQuery ADMIN 역할을 가진 멤버

## 데이터 소스 상세 가이드

### Object Storage 데이터 소스 쿼리 실행

* Object Storage 데이터 소스에 대한 쿼리는 Trino-Hive를 기반으로 수행됩니다.
    * Hive는 [Apache Hadoop](https://hive.apache.org/) 분산 스토리지 환경에서 SQL 작업 처리를 지원하기 위한 솔루션입니다.
* DataQuery에서는 Object Storage 접근을 위해 S3 호환 레이어를 사용하며, 스키마 또는 테이블을 위한 데이터 경로 지정 시 s3a 프로토콜을 사용해야 합니다(ex. s3a://example/test).
* Object Storage상의 Parquet, JSON, ORC, CSV, Text 타입의 데이터에 대한 처리를 지원합니다.
* Object Storage 데이터 소스는 default라는 이름의 기본 스키마를 제공하며, 해당 스키마에서 작업할 수 있습니다.
> [참고]
> Object Storage 쿼리에 사용하는 Hive의 성능 향상이 필요한 경우 고객 센터로 문의하세요.

#### Hive 기능 동작을 위한 부가적인 문법

* Trino-Hive는 기본적으로 표준 SQL 문법을 따르지만 Hive 동작 대응을 위한 부가적인 기능/문법이 존재합니다. [상세 정보](https://trino.io/docs/462/connector/hive.html)
* 지원 데이터 포맷
    * 기본 포맷은 ORC로 지정되어 있으며, 설정으로 Parquet, JSON, ORC, CSV, Text 등을 지정할 수 있습니다.
    * 테이블 생성 시 with절의 format 값으로 지정할 수 있습니다.

``` sql
 CREATE TABLE sample (...) WITH ( format = '타입')
```

* 테이블 종류
    * 내부 테이블(Managed Table)
        * DB 생성 시에 지정된 특정 경로에서(dataquery-warehouse 버킷) 테이블 데이터가 관리됩니다.
        * 테이블을 삭제하면 테이블 정보 및 Object Storage에 저장된 파일도 함께 삭제됩니다.
        * 테이블을 생성할 때 별도의 옵션을 지정하지 않으면 내부 테이블로 생성됩니다.
    * 외부 테이블(External Table)
        * 사용자가 지정한 별도의 경로에 위치한 데이터를 기반으로 동작합니다.
        * 테이블을 삭제할 때 내부 테이블과는 달리 연결된 데이터 원본은 삭제되지 않습니다.
        * 테이블을 생성할 때 WITH절의 external\_location에 데이터의 경로를 지정해야 합니다.
          * external_location 데이터의 경로 입력 시 버킷(컨테이너)명은 [NHN Cloud Object Storage의 버킷 명명 규칙](https://docs.toast.com/ko/Storage/Object%20Storage/ko/s3-api-guide/#_7)을 지켜야 합니다.

``` sql
# Managed Table 샘플
 CREATE TABLE sample (...);
# External Table 샘플
 CREATE TABLE sample (...) WITH ( external_location = 's3a://<버킷,컨테이너명>/<데이터 디렉토리 경로>/');
```

* 파티션(Partition)
    * Hive는 데이터를 특정 기준의 디렉터리로 분리하여 저장할 수 있는 파티션 기능을 제공합니다.
    * 테이블에 파티션을 적용하거나 파티션을 조작하려면 아래와 같은 쿼리가 필요합니다.

``` sql
#테이블에 파티션을 적용하여 생성
CREATE TABLE default.sample (...) WITH ( partitioned_by = ARRAY['columna', 'columnb'],)
#파티션 조회
SELECT * FROM default"sample$partitions"
#파티션을 조작
system.create_empty_partition(schema_name, table_name, partition_columns, partition_values)
system.sync_partition_metadata(schema_name, table_name, mode, case_sensitive)
system.register_partition(schema_name, table_name, partition_columns, partition_values, location)
```
* 파티션 프로시저
  * sync_partition_metadata
    * 오브젝트들의 경로에서 파티션 값을 유추해서 자동으로 파티션 값을 등록, 삭제할 수 있습니다.
      
      | 모드 | 설명                                                                                |
      | ----- |-----------------------------------------------------------------------------------|
      | ADD | 파티션 값이 테이블에 등록되어 있지 않고, Object Storage 오브젝트들이 Hive 파티션 경로에 맞게 존재할 때 파티션 값을 추가합니다. |
      | DROP | 파티션 값이 이미 테이블에 등록되었지만, Object Storage 오브젝트들이 Hive 파티션 경로에 존재하지 않는다면 파티션 값을 삭제합니다. |
      | FULL | ADD, DROP을 차례대로 수행합니다.                                                            |
    * Object Storage 오브젝트들의 경로를 기준으로 Hive 파티션 값을 유추하는 방법은 아래와 같습니다.
      * 정의된 external\_location 하위에 있는 모든 오브젝트를 조회한 뒤 경로를 추출합니다.
      * 파티션 열이 c1 열과 c2 열로 지정되어 있을 경우, Hive 파티션으로 유효한 경로는 `/c1=<c1 값>/c2=<c2 값>`를 포함해야 합니다.
      * 예를 들어 external\_location='s3a://location/tmp/', partitioned_by=ARRAY['year', 'month', 'day'] 로 정의된 테이블이 있을 때, external_location 하위 모든 오브젝트의 경로를 추출한 뒤 그 경로가 s3a://location/tmp/year=yyyy/month=MM/day=dd/와 같은 형식을 포함하면 Hive 파티션 경로로 `유효`하다고 판단하여 파티션 값을 유추합니다.
    * 주의
      * sync_partition_metadata를 실행하려면 테이블에서 정의한 external\_location에 컨테이너 이하 경로가 반드시 하나 더 존재해야 합니다. 예를 들어, external\_location='s3a://location/tmp/'와 같이 컨테이너가 location일 때 하위에 tmp로 경로가 하나 더 있어야 합니다.
  * register_partition
    * 사용자가 지정한 경로를 파티션의 값으로 직접 등록할 수 있습니다.
    * 세 번째 파라미터인 partition_columns에는 Hive 테이블에서 정의한 파티션 열들을 입력합니다.
    * 네 번째 파라미터인 partition_values에는 등록하려는 파티션 값들을 입력합니다.
    * 다섯 번째 파라미터인 location에 오브젝트가 반드시 하나 이상 존재해야 합니다.
* 제약 사항
    * CSV 타입의 테이블 칼럼은 VARCHAR 타입만 지원됩니다.
    * DataQuery에서는 Object Storage 접근을 위해 S3 호환 레이어를 사용하며, 스키마 또는 테이블을 위한 데이터 경로 지정 시 s3a 프로토콜을 사용해야 합니다(ex. s3a://example/test).
    * External table의 external\_location로 지정되는 데이터 디렉터리 경로 객체가 별도로 존재해야 합니다.
        * Object Storage에서 디렉터리를 별도로 생성한 상태에서 데이터가 해당 디렉토리에 위치해야 정상적으로 연동이 될 수 있습니다.
        * 만약 해당 처리에 문제가 있을 경우에는 고객 센터로 문의하십시오.
    * External table의 external\_location 경로명에 한글이 들어갈 경우 정상적으로 데이터가 처리되지 않습니다.
    * 테이블과 연결된 Object Storage 버킷이 삭제되면 테이블 DROP 쿼리가 실패합니다.
    * DELETE, UPDATE는 파티션 데이터에 대해서만 제한적으로 수행할 수 있습니다.
        * [상세 정보](https://trino.io/docs/462/connector/hive.html#data-management)

#### 외부 테이블 쿼리 이용 튜토리얼

1. 샘플 CSV 파일을 [다운로드](https://static.toastoven.net/prod_dataquery/files/facility-boundary-us-all.csv)하여 Object Storage에 업로드합니다.

<img src="https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_dataquery/dataquery_console_04_ko.png"/>

2. Object Storage 콘솔에서 액세스 키, 시크릿 키를 발급 받습니다.
3. Object Storage의 액세스 키, 시크릿 키, 엔드포인트를 이용하여 Object Storage 데이터 소스를 입력합니다.
4. 쿼리 편집기로 이동하여 방금 전 추가한 Object Storage 데이터 소스를 선택하고 default 스키마를 선택합니다.
5. 아래와 같이 CREATE TABLE 쿼리문을 입력하여 실행합니다.

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

6. 테이블이 정상적으로 추가되었는지 확인하기 위해 테이블을 새로 고침합니다.

<img src="https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_dataquery/dataquery_console_05_ko.png" width=220/>

7. 해당 테이블에서 아래와 같이 쿼리를 실행합니다.

``` SQL
SELECT * FROM corona_facility_us
        WHERE facility_place_id = 'ChIJkxHDPsnTQIYR7MH7N-eIdQ0'
          AND facility_latitude = '29.952'
```

8. 총 10건의 데이터가 정상적으로 나오는지 확인합니다.

### MySQL 데이터 소스 쿼리 실행

* MySQL 데이터 소스에 대한 쿼리는 Trino-MySQL을 기반으로 수행됩니다.
* MySQL 데이터 소스의 스키마와 테이블은 소문자명을 기반으로 동작하고 표현됩니다.
* 대소문자가 다른 같은 이름의 테이블이 있으면 쿼리 실행 및 스키마 수집이 정상 동작하지 않을 수 있습니다.
* 제약 사항
    * DELETE는 특정 조건이 충족될 때만 제한적으로 수행할 수 있습니다.
        * where 절이 존재할 때 조건자(Predicate)가 데이터 소스로 온전히 푸시다운(Pushdown)될 수 있어야 합니다.
        * 텍스트 타입의 열은 푸시다운이 지원되지 않습니다.
        * [상세 정보](https://trino.io/docs/462/connector/mysql.html#predicate-pushdown-support)
    * UPDATE는 특정 조건이 충족될 때만 제한적으로 수행할 수 있습니다.
        * 상수 값으로의 할당 및 조건자(Predicate)가 존재할 경우에만 수행할 수 있습니다.
        * 산술 표현식, 함수 호출 및 상수가 아닌 값으로의 UPDATE문은 지원되지 않습니다.
        * 테이블의 모든 열을 동시에 업데이트할 수 없습니다.
        * [상세 정보](https://trino.io/docs/462/connector/mysql.html#update)

### PostgreSQL 데이터 소스 쿼리 실행

* PostgreSQL 데이터 소스에 대한 쿼리는 Trino-PostgreSQL을 기반으로 수행됩니다.
* PostgreSQL 데이터 소스의 스키마와 테이블은 소문자명을 기반으로 동작하고 표현됩니다.
* 대소문자가 다른 같은 이름의 테이블이 있으면 쿼리 실행 및 스키마 수집이 정상 동작하지 않을 수 있습니다.
* 제약 사항
    * DELETE는 특정 조건이 충족될 때만 제한적으로 수행할 수 있습니다.
        * where 절이 존재할 때 조건자(Predicate)가 데이터 소스로 온전히 푸시다운(Pushdown)될 수 있어야 합니다.
        * CHAR 또는 VARCHAR와 같은 문자열 유형에 대한 범위 조건(>, < 또는 BETWEEN)은 푸시다운이 지원되지 않습니다.
        * 텍스트 타입에 대한 동등 비교 조건(IN, =, !=)은 푸시다운이 지원됩니다.
        * [상세 정보](https://trino.io/docs/462/connector/postgresql.html#predicate-pushdown-support)
    * UPDATE는 특정 조건이 충족될 때만 제한적으로 수행할 수 있습니다.
        * 상수 값으로의 할당 및 조건자(Predicate)가 존재할 경우에만 수행할 수 있습니다.
        * 산술 표현식, 함수 호출 및 상수가 아닌 값으로의 UPDATE문은 지원되지 않습니다.
        * 테이블의 모든 열을 동시에 업데이트할 수 없습니다.
        * [상세 정보](https://trino.io/docs/462/connector/postgresql.html#update)

### Oracle 데이터 소스 쿼리 실행

* Oracle 데이터 소스에 대한 쿼리는 Trino-Oracle을 기반으로 수행됩니다.
* Oracle 데이터 소스의 스키마와 테이블은 소문자명을 기반으로 동작하고 표현됩니다.
* 대소문자가 다른 같은 이름의 테이블이 있으면 쿼리 실행 및 스키마 수집이 정상 동작하지 않을 수 있습니다.
* 제약 사항
    * DELETE, UPDATE는 특정 조건이 충족될 때만 제한적으로 수행할 수 있습니다.
        * where 절이 존재할 때 조건자(Predicate)가 데이터 소스로 온전히 푸시다운(Pushdown)될 수 있어야 합니다.
        * CLOB, NCLOB, BLOB, or RAW(n)인 Oracle 타입의 열은 푸시다운이 지원되지 않습니다.
        * [상세 정보](https://trino.io/docs/462/connector/oracle.html#predicate-pushdown-support)
    * UPDATE는 특정 조건이 충족될 때만 제한적으로 수행할 수 있습니다.
        * 상수 값으로의 할당 및 조건자(Predicate)가 존재할 경우에만 수행할 수 있습니다.
        * 산술 표현식, 함수 호출 및 상수가 아닌 값으로의 UPDATE문은 지원되지 않습니다.
        * 테이블의 모든 열을 동시에 업데이트할 수 없습니다.
        * [상세 정보](https://trino.io/docs/462/connector/oracle.html#update)

### EDB 데이터 소스 쿼리 실행

* EDB 데이터 소스에 대한 쿼리는 Trino-PostgreSQL을 기반으로 수행됩니다.
* EDB 데이터 소스의 스키마와 테이블은 소문자명을 기반으로 동작하고 표현됩니다.
* 대소문자가 다른 같은 이름의 테이블이 있으면 쿼리 실행 및 스키마 수집이 정상 동작하지 않을 수 있습니다.
* 제약 사항
    * DELETE는 특정 조건이 충족될 때만 제한적으로 수행할 수 있습니다.
        * where 절이 존재할 때 조건자(Predicate)가 데이터 소스로 온전히 푸시다운(Pushdown)될 수 있어야 합니다.
        * CHAR 또는 VARCHAR와 같은 문자열 유형에 대한 범위 조건(>, < 또는 BETWEEN)은 푸시다운이 지원되지 않습니다.
        * 텍스트 타입에 대한 동등 비교 조건(IN, =, !=)은 푸시다운이 지원됩니다.
        * [상세 정보](https://trino.io/docs/462/connector/postgresql.html#predicate-pushdown-support)
    * UPDATE는 특정 조건이 충족될 때만 제한적으로 수행할 수 있습니다.
        * 상수 값으로의 할당 및 조건자(Predicate)가 존재할 경우에만 수행할 수 있습니다.
        * 산술 표현식, 함수 호출 및 상수가 아닌 값으로의 UPDATE문은 지원되지 않습니다.
        * 테이블의 모든 열을 동시에 업데이트할 수 없습니다.
        * [상세 정보](https://trino.io/docs/462/connector/postgresql.html#update)

### MariaDB 데이터 소스 쿼리 실행

* MariaDB 데이터 소스에 대한 쿼리는 Trino-MariaDB를 기반으로 수행됩니다.
* MariaDB 데이터 소스의 스키마와 테이블은 소문자명을 기반으로 동작하고 표현됩니다.
* 대소문자가 다른 같은 이름의 테이블이 있으면 쿼리 실행 및 스키마 수집이 정상 동작하지 않을 수 있습니다.
* 제약 사항
    * DELETE는 특정 조건이 충족될 때만 제한적으로 수행할 수 있습니다.
        * where 절이 존재할 때 조건자(Predicate)가 데이터 소스로 온전히 푸시다운(Pushdown)될 수 있어야 합니다.
        * 텍스트 타입의 열은 푸시다운이 지원되지 않습니다.
        * [상세 정보](https://trino.io/docs/462/connector/mariadb.html#predicate-pushdown-support)
    * UPDATE는 특정 조건이 충족될 때만 제한적으로 수행할 수 있습니다.
        * 상수 값으로의 할당 및 조건자(Predicate)가 존재할 경우에만 수행할 수 있습니다.
        * 산술 표현식, 함수 호출 및 상수가 아닌 값으로의 UPDATE문은 지원되지 않습니다.
        * 테이블의 모든 열을 동시에 업데이트할 수 없습니다.
        * [상세 정보](https://trino.io/docs/462/connector/mariadb.html#update)


### Iceberg 데이터 소스 쿼리 실행

* Iceberg 데이터 소스에 대한 쿼리는 Trino-Iceberg를 기반으로 수행됩니다.
* Object Storage에 존재하는 Iceberg 테이블 데이터 및 지원하는 포맷의 데이터에 대해 연동할 수 있습니다.
    * PARQUET(기본 포맷), ORC, AVRO 타입의 데이터를 지원합니다.
* Object Storage 접근을 위해 S3 호환 레이어를 사용하며, 스키마 또는 테이블을 위한 데이터 경로 지정 시 s3a 프로토콜을 사용해야 합니다(예: s3a://example/test).

#### 스키마

* CREATE SCHEMA 문을 통해 생성할 수 있습니다.

```sql
# 기본 경로에 스키마 생성
CREATE SCHEMA example_schema;
# 지정 경로에 스키마 생성
CREATE SCHEMA example_schema
WITH (location = 's3a://my-bucket/example_schema/');
```

#### 테이블

* CREATE TABLE 또는 CREATE TABLE AS 문을 통해 생성할 수 있습니다.
* 테이블 속성 지정으로 테이블에 대한 메타데이터를 설정할 수 있습니다.
    * 테이블 속성은 WITH 절을 사용하여 지정할 수 있습니다.

```sql
CREATE TABLE example_table (c1 INTEGER, c2 DATE, c3 DOUBLE);
## 속성 지정
CREATE TABLE example_table (c1 INTEGER, c2 DATE, c3 DOUBLE)
WITH (
    format = 'PARQUET',
    partitioning = ARRAY['c1', 'c2'],
    sorted_by = ARRAY['c3'],
    location = 's3a://my-bucket/example_schema/example_table/'
);
```

* 테이블 속성
    * 테이블에 대한 메타데이터를 설정할 수 있습니다. [추가 정보](https://trino.io/docs/462/connector/iceberg.html#table-properties)

| 속성 이름 | 설명 |
| ----- | --- |
| format | 테이블 데이터 파일의 형식을 지정합니다. PARQUET, ORC, 또는 AVRO. <br> 기본값은 PARQUET입니다. |
| partitioning | 테이블 파티션을 지정합니다. 테이블이 c1 열과 c2 열로 분할된 경우 partitioning=ARRAY['c1', 'c2']로 지정할 수 있습니다. |
| sorted\_by | 개별 데이터 파일 저장 시 지정한 열의 값으로 정렬하여 저장합니다. |
| location | 테이블에 대한 Object Storage 경로를 지정합니다.<br>속성을 설정하지 않을 경우 기본 경로 하위의 스키마 경로에 저장됩니다. |

#### 파티션

* 테이블 속성을 통해 테이블 데이터가 분할 저장된 구조의 분할된(파티션된) 테이블을 만들 수 있습니다.
    * 파티션 열이 c1 열과 c2 열로 지정되어 있을 경우, 해당 파티션의 데이터는 테이블 데이터 경로 하위의 `/c1=<c1 값>/c2=<c2 값>`에 저장됩니다.
* Iceberg는 쓰기(write)된 데이터의 값을 통해 파티션을 자동으로 관리해 주기 때문에 파티션을 수동으로 추가/관리할 수 없습니다.
* 테이블 열을 이용(변환)하여 파티션을 지정할 수 있는 기능을 지원합니다.
    * year, month, day, hour, bucket, truncate [추가 정보](https://trino.io/docs/462/connector/iceberg.html#partitioned-tables)

| 변환 | 지원 유형 | 설명 |
| --- | ----- | --- |
| year(ts) | DATE, TIMESTAMP | 연도별 |
| month(ts) | DATE, TIMESTAMP | 월별 |
| day(ts) | DATE, TIMESTAMP | 일별 |
| hour(ts) | TIMESTAMP | 시간별 |

#### 메타데이터 테이블

* 메타데이터 테이블을 조회하여 Iceberg 테이블의 메타정보를 확인할 수 있습니다. [추가 정보](https://trino.io/docs/462/connector/iceberg.html#metadata-tables)
    * $properties
        * 테이블 속성
    * $history
        * 테이블의 메타데이터가 변경된 이력
    * $snapshots
        * 데이터에 변화가 발생할 때 기록된 테이블 형상 이력
    * $manifests
        * 데이터 파일의 묶음을 관리하는 파일의 정보
    * $partitions
        * 테이블의 상세한 파티션 정보
    * $files
        * 현재 테이블의 스냅숏

```sql
## 테이블 속성 조회
SELECT * FROM "test_table$properties"
```

#### 데이터 관리

* 테이블 등록
    * 이미 파일로 존재하는 Iceberg 테이블이 존재하지만 등록되지 않은 Iceberg 테이블을 등록하는 방법입니다.
    * register\_table을 호출하여 등록할 수 있습니다.

```sql
CALL example.system.register_table(schema_name => 'example_schema', table_name => 'example_table', table_location => 's3a://my-bucket/example_schema/example_table')
```

* 테이블 삭제
    * DROP TABLE 문을 통해 테이블을 삭제할 수 있습니다. 이 명령은 실제 Iceberg 데이터를 삭제합니다.
* 테이블 제외
    * 테이블을 삭제(DROP) 하지 않고 테이블 목록에서만 제외할 때 사용할 수 있습니다.

```sql
CALL example.system.unregister_table(schema_name => 'example_schema', table_name => 'example_table')
```

* 스키마 진화(schema evolution)
    * Iceberg는 메타데이터만을 변경하는 스키마 진화을 지원합니다. 스키마 업데이트를 수행할 때 데이터 파일 자체가 변경되지 않습니다.
    * 열 추가, 삭제, 재정렬, 이름 변경, 타입 변경을 지원합니다.
    * 타입 변경은 기존 타입에서 확장되는 타입의 변경만 지원합니다.
        * INTEGER에서 BIGINT
        * REAL에서 DOUBLE
        * DECIMAL의 정밀도 증가
* 스냅숏 정리
    * 쓰기, 변경, 압축 등으로 인해 생성된 스냅숏을 정리합니다.
    * 불필요해진 정보와 데이터 파일을 제거하여 메타데이터의 크기를 유지할 수 있습니다.
    * 테이블 메타데이터의 크기를 작게 유지하려면 스냅숏을 정기적으로 정리하는 것이 좋습니다.

```sql
ALTER TABLE test_table EXECUTE expire_snapshots(retention_threshold => '7d')
```

* 고아 파일 정리
    * 현재 존재하는 메타데이터와 관련이 없어진 데이터 파일을 삭제합니다.
        * 해당 파일들 중에 지정 시간 이전에 생성된 대상을 삭제합니다.
    * 테이블의 데이터 디렉터리 크기를 관리하려면 파일을 정리하는 것이 좋습니다.

```sql
ALTER TABLE test_table EXECUTE remove_orphan_files(retention_threshold => '7d')
```

#### Iceberg 타입 맵핑 정보

* Iceberg 타입은 DataQuery에서 처리할 수 있는 타입으로 아래와 같이 맵핑됩니다.

| DataQuery 타입 | Iceberg 타입 |
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

#### Object Storage에 존재하는 Parquet 파일을 Iceberg 테이블에 추가
* 특정 파일 혹은 특정 경로 하위의 파일들을 Iceberg 테이블에 데이터로 추가할 수 있습니다.
* 파티션이 없는 테이블은 add_files, 파티션이 정의된 테이블은 add_files_with_partition으로 데이터 파일과 파티션 값을 추가할 수 있습니다.
* add_files 프로시저

  |인자  | 지원하는 값                    | 설명                                                                                                                                                                                     |
  | --- |---------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | location | 데이터 파일 경로                 | 추가하려는 데이터 파일 경로                                                                                                                                                                        |
  | format | PARQUET(기본 포맷), ORC, AVRO | 추가하려는 데이터 파일 포맷                                                                                                                                                                        |
  | recursive_directory | FAIL(기본 값), TRUE, FALSE   | location 이하 경로를 재귀로 탐색할 수 있을 때의 동작<br>FAIL => 입력한 데이터 파일 경로가 2단계 깊이로 재귀 탐색이 가능하다면 쿼리를 실패하게 합니다.<br> TRUE => 입력한 데이터 파일 경로 하위를 재귀로 모두 탐색합니다.<br>FALSE => 입력한 데이터 파일 경로 2단계 깊이부터는 무시합니다. |
  |duplicate_file  | FAIL(기본 값), SKIP, ADD     | 등록하려는 데이터 파일이 이미 등록된 iceberg 테이블의 데이터 파일과 중복일 때의 동작<br>FAIL => iceberg 테이블에 이미 등록된 데이터 파일과 비교해서 중복된 데이터 파일이 있으면 쿼리 실패합니다.<br>SKIP => 중복된 파일은 무시합니다.<br>ADD => 데이터 파일을 추가합니다.           |
```sql
## example_table에 mybucket/a/path 하위 데이터 파일을 추가
ALTER TABLE example.system.example_table 
EXECUTE add_files(location => 's3://my-bucket/a/path', format => 'PARQUET', recursive_directory => 'FAIL', duplicate_file => 'FAIL')
```
* add_files_with_partition 프로시저
  * 파티션 변형을 정의한 테이블도 지원합니다.
  * 등록하려는 파티션 열 타입이 DATE일 때는 `YYYY-MM-DD`, TIMESTAMP일 때는`YYYY-MM-DD HH:mm:ss`의 형식으로 입력해야 합니다. timezone이 있는 TIMESTAMP인 경우 `YYYY-MM-DD HH:mm:ss Asia/Seoul`과 같이 끝에 zoneId가 명시되어야 합니다.
 
    |인자  | 지원하는 값                    | 설명                                                                                                                                                                                      |
    | --- |---------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | location | 데이터 파일 경로                 | 추가하려는 데이터 파일 경로                                                                                                                                                                         |
    |partition_columns| ARRAY['partition_column'] | iceberg 테이블에 정의된 파티션 열을 나열하며 테이블이 c1, c2열로 분할된 경우 ARRAY['c1', 'c2']로 입력                                                                                                                 |
    |partition_values| ARRAY['partition_value']  | 등록하려는 파티션 값                                                                                                                                                                             |
    | format | PARQUET(기본 포맷), ORC, AVRO | 추가하려는 데이터 파일의 포맷                                                                                                                                                                        |
    | recursive_directory | FAIL(기본 값), TRUE, FALSE   | location 이하 경로를 재귀로 탐색할 수 있을 때의 동작<br>FAIL => 입력한 데이터 파일 경로가 2단계 깊이로 재귀 탐색이 가능하다면 쿼리를 실패하게 합니다.<br> TRUE => 입력한 데이터 파일 경로 하위를 재귀로 모두 탐색합니다.<br>FALSE => 입력한 데이터 파일의 경로 2단계 깊이부터는 무시합니다. |
    |duplicate_file  | FAIL(기본 값), SKIP, ADD     | 등록하려는 데이터 파일이 이미 등록된 iceberg 테이블의 데이터 파일과 중복일 때의 동작<br>FAIL => iceberg 테이블에 이미 등록된 데이터 파일과 비교해서 중복된 데이터 파일이 있으면 쿼리 실패합니다.<br>SKIP => 중복된 파일은 무시합니다.<br>ADD => 데이터 파일을 추가합니다.            |
```sql
## 파티션 열이 year이면서 day 변환이 적용된 iceberg 테이블
ALTER TABLE example.system.example_table 
EXECUTE add_files_with_partition(location => 's3://my-bucket/a/path', partition_columns => ARRAY['year'], partition_values => ARRAY['2024-11-21'], format => 'PARQUET', recursive_directory => 'TRUE', duplicate_file => 'FAIL')
```
#### 주의 및 제약 사항

* 동일 경로에 Iceberg 테이블을 중복해서 생성하는 것은 불가능합니다.
* 열을 변환하여 파티션을 구성할 때, 동일한 열을 사용할 수 없습니다.
    * 예: 하나의 DATE 타입을 가지는 열로 year, month 두 개의 파티션을 설정할 수 없습니다.

#### FAQ

* 이미 Object Storage에 Iceberg 데이터가 존재합니다. 어떻게 DataQuery에 적용할 수 있나요?
    * register_table을 실행하여 등록할 수 있습니다. 데이터 관리 > 테이블 등록을 확인하세요.
* Object Storage에는 Parquet 파일만 존재합니다. 어떻게 Iceberg 테이블로 만들 수 있나요?
    * Iceberg 테이블을 생성한 뒤, add_files, add_files_with_partition 프로시저를 사용하여 데이터를 추가할 수 있습니다.
* 이미 존재하는 Iceberg 테이블에 Parquet 데이터만 추가하고 싶습니다.
    * add_files, add_files_with_partition 프로시저를 사용하여 데이터를 추가할 수 있습니다.


## 외부 연동
### Trino cli

* 설정 메뉴를 통해 발급 받은 인증 정보, 접속 정보와 Trino에서 지원하는 CLI 툴을 통해 커맨드라인에서 쿼리를 실행할 수 있습니다.
  * DataQuery는 현재 Trino 462 버전을 기반으로 서비스하고 있습니다.
  * [Trino CLI](https://repo1.maven.org/maven2/io/trino/trino-cli/462/trino-cli-462-executable.jar)

```
# 파일에 실행 권한이 필요합니다. chmod +x로 부여할 수 있습니다.
# 예: chmod +x trino-cli-462-executable.jar

./trino-cli-462-executable.jar --server <접속URL(필수)> \
  --user <아이디(필수)> --password \
  --catalog <데이터 소스 이름> \
  --schema <스키마 이름>
```

* 설정 파라미터
    * 접속 URL(필수)
        * 설정 화면에서 제공 받은 접속 URL (ex. [https://x-x-x-x-x.kr1-cluster-dataquery.nhncloudservice.com](https://x-x-x-x-x.kr1-cluster-dataquery.nhncloudservice.com))
    * 아이디(필수)
        * 인증 정보 화면에서 제공 받은 아이디
    * 비밀번호(필수)
        * 인증 정보 화면에서 제공 받은 비밀번호
        * 커맨드를 실행하면 나오는 프롬프트 창에서 입력하거나 `export TRINO_PASSWORD=<비밀번호>`로 비밀번호를 미리 설정할 수 있습니다.
    * 데이터 소스 이름
        * 연결한 데이터 소스 이름
    * 스키마 이름
        * 연결한 스키마 이름
* `--debug`옵션을 추가하여 디버그 정보를 추가로 출력할 수 있습니다.
* catalog, schema 값은 명령을 수행할 연결에 대한 값으로, 입력하지 않아도 cli를 실행할 수 있으며 아래 쿼리를 이용해 catalog나 schema 목록을 확인할 수 있습니다.
    * show catalogs
    * show schemas
* 더 자세한 정보는 [Trino 가이드 페이지](https://trino.io/docs/462/client/cli.html)를 참고하세요.

### JDBC 연결

* **설정** 메뉴에서 발급 받은 인증 정보, 접속 정보와 Trino에서 지원하는 JDBC 드라이버를 이용해 JDBC에 연결할 수 있습니다.

```
jdbc:trino://${host}:${port}
jdbc:trino://${host}:${port}/${catalog}
jdbc:trino://${host}:${port}/${catalog}/${schema}
```

* 설정 파라미터
    * host(필수)
        * 설정 화면에서 제공 받은 접속 URL에서 `https://`를 제외한 나머지를 입력합니다(ex . x-x-x-x-x.kr1-cluster-dataquery.nhncloudservice.com).
    * port(필수)
        * 443을 입력합니다.
    * catalog
        * 연결을 원하는 데이터 소스 이름
    * schema
        * 연결을 원하는 스키마 이름
* 접속 정보 예시
    * jdbc:trino://test-dataquery-domain-12345abcd.kr1-cluster-dataquery.nhncloudservice.com:443/catalog/schema
* 더 자세한 정보는 [Trino JDBC 가이드 페이지](https://trino.io/docs/462/client/jdbc.html)를 참고하세요.