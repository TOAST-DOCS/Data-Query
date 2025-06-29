## Data & Analytics > DataQuery > Release Notes
### June 24, 2025
#### Added Features
* Added a visualization area for the cluster status metrics.
  * Status will be collected for clusters that were started after June 24, 2025.

### May 27, 2025
#### Added Features
* Added the feature to set the instance type of a metastore to work with Object Storage data sources.

### January 21, 2025
#### Feature Updates
* Upgraded DataQuery to service based on Trino 462 version.
* Added the add_files_with_partition function for iceberg connector.

### October 29, 2024
#### Trino Version Upgrade
* Upgraded DataQuery to work based on Trino 455 version. 
* Made performance improvements and bug fixes for some queries.

#### Added Features
* Added Iceberg to the data source type.

### July 23, 2024
#### Feature Updates
* Improved to send email notifications for disabling integration when Object Storage credentials for storing query history expire.

### June 25, 2024
#### Added Features
* Added MariaDB to the data source types.
* The query history save feature has been added.

### May 28, 2024
#### Feature Updates
* Changed the storage period for query information to 90 days.

### May 1, 2024
#### Feature Updates
* Changed the maximum registration number of Object Storage data sources to five.
* Removed the minimum registration limit for Object Storage data sources.

### February 27, 2024
#### Feature Updates
- Added the feature to save and manage frequently used queries.

### January 23, 2024   
#### Trino Version Upgrade
* Upgraded the Trino version provided by DataQuery from 398 to 434.
* Added PostgreSQL, Oracle, and EDB to data source types.

### October 31, 23
#### Feature Updates
* Added a feature to select a cluster type

### December 27, 2022

#### Release of a New Service

* DataQuery is a service that runs queries on large data based on Distributed SQL Query Engine Trino.
* Supports NHN Cloud Object Storage and NHN Cloud RDS for MySQL with data sources.
