## DataQuery Overview

* DataQuery is a service that runs queries on large data based on Distributed SQL Query Engine Trino.
* Supports connection with NHN Cloud Services such as Object Storage.

## Main Features

* Supports connection to data sources such as NHN Cloud Object Storage and NHN Cloud RDS for MySQL.
* Integrated Queries can be run in standard SQL for different data sources.
* You can run queries in the web console.
* Provides preview and download features for web console query results.
* Provides information and history about running or completed queries.
* Trino endpoint provides UI access and linking with external tools (JDBC, CLI, BI solutions, etc.).
* Provides user project-specific Trino clusters and allows for specification adjustment when required.

## Service Terminology 

| Terms | Descriptions |
| --- | --- |
| Data source | Refers to database or dataset for use in DataQuery. |
| Catalog | Includes schema and services as a reference to data sources through connectors. |
| Schema | Configures a table and defines a table that can be queried with catalog. It has the same concept as DB in typical RDBMS. |
| Table | Collection of data consisting of rows and columns. |
| Cluster | Refers to Trino cluster. |