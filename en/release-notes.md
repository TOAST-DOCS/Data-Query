<a id="data-analytics-dataquery-release-notes"></a>
## Data & Analytics > DataQuery > Release Notes { #data-analytics-dataquery-release-notes }

<a id="may-27-2026"></a>
## May 27, 2026 { #may-27-2026 }

<a id="added-integration-services"></a>
### Added Integration Services { #added-integration-services }

* Added Data Lake Storage as a data source type.

<a id="april-28-2026"></a>
## April 28, 2026 { #april-28-2026 }

<a id="april-28-2026-added-integration-services"></a>
### Added Integration Services { #april-28-2026-added-integration-services }

<!-- pre-align: ko에 대응 섹션 없음 — 검토 필요 (Spurious duplicate of parent date heading t4 ('April 28, 2026') inserted at L3; no ko counterpart exists) -->
### April 28, 2026
<!-- pre-align: ko에 대응 섹션 없음 — 검토 필요 (Child of spurious t6; semantically duplicates t5 which already matches k5; no ko counterpart exists) -->
#### Added integration service
* Added a "Scheduled Query" template to the Cloud Scheduler service.
  * Queries can now be run on a desired schedule using the template.

<a id="march-24-2026"></a>
## March 24, 2026 { #march-24-2026 }

<a id="feature-updates"></a>
### Feature Updates { #feature-updates }

* Improved the console query result display policy
  * Removed the limit that restricted console query results to within 1 MB and 5,000 rows.
  * Made improvements so that console query results can now display up to 30 MB.
  * Added buttons to view and copy console query results.

<a id="september-23-2025"></a>
## September 23, 2025 { #september-23-2025 }

<a id="trino-version-upgrade"></a>
### Trino version Upgrade { #trino-version-upgrade }

* Upgraded DataQuery to service based on Trino 476 version.
* Made performance improvements and bug fixes for some queries.

<a id="june-24-2025"></a>
## June 24, 2025 { #june-24-2025 }

<a id="added-features"></a>
### Added Features { #added-features }

* Added a visualization area for the cluster status metrics.
  * Status will be collected for clusters that were started after June 24, 2025.

<a id="may-27-2025"></a>
## May 27, 2025 { #may-27-2025 }

<a id="may-27-2025-added-features"></a>
### Added Features { #may-27-2025-added-features }

* Added the feature to set the instance type of a metastore to work with Object Storage data sources.

<a id="january-21-2025"></a>
## January 21, 2025 { #january-21-2025 }

<a id="january-21-2025-feature-updates"></a>
### Feature Updates { #january-21-2025-feature-updates }

* Upgraded DataQuery to service based on Trino 462 version.
* Added the add_files_with_partition function for iceberg connector.

<a id="october-29-2024"></a>
## October 29, 2024 { #october-29-2024 }

<a id="october-29-2024-trino-version-upgrade"></a>
### Trino Version Upgrade { #october-29-2024-trino-version-upgrade }

* Upgraded DataQuery to work based on Trino 455 version. 
* Made performance improvements and bug fixes for some queries.

<a id="october-29-2024-added-features"></a>
### Added Features { #october-29-2024-added-features }
* Added Iceberg to the data source type.

<a id="july-23-2024"></a>
## July 23, 2024 { #july-23-2024 }

<a id="july-23-2024-feature-updates"></a>
### Feature Updates { #july-23-2024-feature-updates }

* Improved to send email notifications for disabling integration when Object Storage credentials for storing query history expire.

<a id="june-25-2024"></a>
## June 25, 2024 { #june-25-2024 }

<a id="june-25-2024-added-features"></a>
### Added Features { #june-25-2024-added-features }

* Added MariaDB to the data source types.
* The query history save feature has been added.

<a id="may-28-2024"></a>
## May 28, 2024 { #may-28-2024 }

<a id="may-28-2024-feature-updates"></a>
### Feature Updates { #may-28-2024-feature-updates }

* Changed the storage period for query information to 90 days.

<a id="may-1-2024"></a>
## May 1, 2024 { #may-1-2024 }

<a id="may-1-2024-feature-updates"></a>
### Feature Updates { #may-1-2024-feature-updates }

* Changed the maximum registration number of Object Storage data sources to five.
* Removed the minimum registration limit for Object Storage data sources.

<a id="february-27-2024"></a>
## February 27, 2024 { #february-27-2024 }

<a id="february-27-2024-feature-updates"></a>
### Feature Updates { #february-27-2024-feature-updates }

* Added the feature to save and manage frequently used queries.

<a id="january-23-2024"></a>
## January 23, 2024 { #january-23-2024 }

<a id="january-23-2024-trino-version-upgrade"></a>
### Trino Version Upgrade { #january-23-2024-trino-version-upgrade }

* Upgraded the Trino version provided by DataQuery from 398 to 434.
* Added PostgreSQL, Oracle, and EDB to data source types.

<a id="october-31-23"></a>
## October 31, 23 { #october-31-23 }

<a id="october-31-23-feature-updates"></a>
### Feature Updates { #october-31-23-feature-updates }

* Added a feature to select a cluster type.

<a id="december-27-2022"></a>
## December 27, 2022 { #december-27-2022 }

<a id="release-of-a-new-service"></a>
### Release of a New Service { #release-of-a-new-service }

* DataQuery is a service that runs queries on large data based on Distributed SQL Query Engine Trino.
* Supports NHN Cloud Object Storage and NHN Cloud RDS for MySQL with data sources.
