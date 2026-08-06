<!-- machine_translated: true -->

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

* Added a "Scheduled Query" template to the Cloud Scheduler service.
  * Queries can now be run on a desired schedule using the template.

<a id="march-24-2026"></a>
## March 24, 2026 { #march-24-2026 }

<a id="feature-updates"></a>
### Feature Updates { #feature-updates }

* Improved the query result display policy in the console
  * Removed the limit that displayed query results run in the console to within 1 MB and 5,000 rows.
  * Improved to display query results run in the console up to 30 MB.
  * Added buttons to view and copy console query results.

<a id="september-23-2025"></a>
## September 23, 2025 { #september-23-2025 }

<a id="trino-version-upgrade"></a>
### Trino Version Upgrade { #trino-version-upgrade }

* Upgraded DataQuery to be served based on Trino version 476.
* Includes performance improvements and bug fixes for some queries.

<a id="june-24-2025"></a>
## June 24, 2025 { #june-24-2025 }

<a id="added-features"></a>
### Added Features { #added-features }

* Added a status metrics visualization area for clusters.
  * Collects the status of clusters started after June 24, 2025.

<a id="may-27-2025"></a>
## May 27, 2025 { #may-27-2025 }

<a id="may-27-2025-added-features"></a>
### Added Features { #may-27-2025-added-features }

* Added the feature to set the instance type of a metastore to work with Object Storage data sources.

<a id="january-21-2025"></a>
## January 21, 2025 { #january-21-2025 }

<a id="january-21-2025-feature-updates"></a>
### Feature Updates { #january-21-2025-feature-updates }

* Upgraded DataQuery to be served based on Trino version 462.
* Added the add_files_with_partition function to the Iceberg connector.

<a id="october-29-2024"></a>
## October 29, 2024 { #october-29-2024 }

<a id="october-29-2024-trino-version-upgrade"></a>
### Trino Version Upgrade { #october-29-2024-trino-version-upgrade }

* Upgraded DataQuery to be served based on Trino version 455.
* Includes performance improvements and bug fixes for some queries.

<a id="october-29-2024-added-features"></a>
### Added Features { #october-29-2024-added-features }

* Added Iceberg as a data source type.

<a id="july-23-2024"></a>
## July 23, 2024 { #july-23-2024 }

<a id="july-23-2024-feature-updates"></a>
### Feature Updates { #july-23-2024-feature-updates }

* Updated to send an integration disabled notification email when the Object Storage authentication credentials for saving Query History expire.

<a id="june-25-2024"></a>
## June 25, 2024 { #june-25-2024 }

<a id="june-25-2024-added-features"></a>
### Added Features { #june-25-2024-added-features }

* Added MariaDB as a data source type.
* Added a feature to save Query History.

<a id="may-28-2024"></a>
## May 28, 2024 { #may-28-2024 }

<a id="may-28-2024-feature-updates"></a>
### Feature Updates { #may-28-2024-feature-updates }

* Changed the retention period for query information to 90 days.

<a id="may-1-2024"></a>
## May 1, 2024 { #may-1-2024 }

<a id="may-1-2024-feature-updates"></a>
### Feature Updates { #may-1-2024-feature-updates }

* Changed the maximum registration limit for Object Storage data sources to 5.
* Removed the minimum registration limit for Object Storage data sources.

<a id="february-27-2024"></a>
## February 27, 2024 { #february-27-2024 }

<a id="february-27-2024-feature-updates"></a>
### Added Features { #february-27-2024-feature-updates }

* Added a feature to save and manage frequently used queries.

<a id="january-23-2024"></a>
## January 23, 2024 { #january-23-2024 }

<a id="january-23-2024-trino-version-upgrade"></a>
### Trino Version Upgrade { #january-23-2024-trino-version-upgrade }

* Upgraded the Trino version provided by DataQuery from 398 to 434.
* Added PostgreSQL, Oracle, and EDB as data source types.

<a id="october-31-23"></a>
## October 31, 2023 { #october-31-23 }

<a id="october-31-23-feature-updates"></a>
### Feature Updates { #october-31-23-feature-updates }

* Added a feature to select the cluster type.

<a id="december-27-2022"></a>
## December 27, 2022 { #december-27-2022 }

<a id="release-of-a-new-service"></a>
### New Service Release { #release-of-a-new-service }

* A service that enables you to run queries on large-scale data based on Trino, a Distributed SQL Query Engine.
* Supports NHN Cloud Object Storage and NHN Cloud RDS for MySQL as data sources.