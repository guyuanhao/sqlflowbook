---
description: >-
  https://github.com/sqlparser/sqlflow_public/blob/master/sqlflow_guide_cn.md#job-list
---

# Job Management

## Job list

<figure><img src="../../.gitbook/assets/185734108-5dc282df-0b49-4061-af2d-c9fa21ab885a.png" alt=""><figcaption></figcaption></figure>

## Create a job

<figure><img src="../../.gitbook/assets/185737736-814ae584-ab72-4be6-a4f6-6393607d385f.gif" alt=""><figcaption></figcaption></figure>

### Click the Job Creation button in the Job List Section

<figure><img src="../../.gitbook/assets/20221101205559.png" alt=""><figcaption></figcaption></figure>

### Enter the Job creation parameters&#x20;

<figure><img src="../../.gitbook/assets/Screenshot from 2022-11-01 21-00-58.png" alt=""><figcaption></figcaption></figure>

### Job sources

Job source can be from one of the following sources:

`upload file`: The data lineage will be generated from the sql meta file you upload(DDL file for an example). Check our [Ingester tool](broken-reference) if you want use this way but don't have compatible sql metadata file.

`from database`: Directly connect to a database server to retrieve the data lineage. You need to give the connection paramters in this mode.

`upload file + database metadata`: Use the above two methods to create the Job together. You may need to use this mode when your data are distracted in different systems.

`dbt`: Read from dbt, the manifest.json and the catalog.json will be required.

`redshift log`: Read from your redshift log.

`snowflake query history`: Read from your snowflake query history. Check [here](job-management.md#snowflake-query-history) for the query history parameter details.\


<figure><img src="../../.gitbook/assets/Screenshot from 2022-11-01 21-01-59.png" alt=""><figcaption></figcaption></figure>

### Default server/database/schema

Give the default value for server/database/schema when there's no related metadata to the database units(such as table,view etc...). If the default values are given here, will use the given values. Otherwise will use `default` as the value for server/database/schema if the default server/database/schema is not set.

<figure><img src="../../.gitbook/assets/Screenshot from 2022-11-01 21-22-38.png" alt=""><figcaption></figcaption></figure>

### Job Type

Choose the Job type when creating the Job. Read more on the [Job type](../getting-started/different-modes-in-gudu-sqlflow/job-mode.md).

<figure><img src="../../.gitbook/assets/Screenshot from 2022-11-01 21-04-21.png" alt=""><figcaption></figcaption></figure>

### Advanced

Customize the extraction/exclusion content under the `advanced` section

<figure><img src="../../.gitbook/assets/Screenshot from 2022-11-01 21-06-07.png" alt=""><figcaption></figcaption></figure>

### Configurable parameters

Give the configurable parameters under the `setting` section. Check [here](../getting-started/different-modes-in-gudu-sqlflow/job-mode.md#simple-job) to get more details for these parameters.

<figure><img src="../../.gitbook/assets/Screenshot from 2022-11-01 21-08-42.png" alt=""><figcaption></figcaption></figure>

### Snowflake query history

<figure><img src="../../.gitbook/assets/Screenshot from 2022-11-03 00-30-54.png" alt=""><figcaption></figcaption></figure>

`enableQueryHistory`: Fetch SQL queries from the query history if set to `true`.

`blockOfTimeInMinutes`: When `enableQueryHistory`is set to true, the interval at which the SQL query was extracted in the query History.

`queryHistorySqlType`: Specify what's kind of SQL statements need to be sent to the SQLFlow for furhter processing after fetch the queries from the Snowflake query history. If `queryHistorySqlType` is specified, will only pickup those SQL statement type and send it the SQLFlow for furhter processing. This can be useful when you only need to discover lineage from a specific type of SQL statements. If `queryHistorySqlType` is empty, all queries fetched from the query history will be sent to the SQLFlow server.

`excludedHistoryDbsSchemas`: List of databases and schemas to exclude from extraction, separated by commas `database1.schema1,database2`.

`duplicateQueryHistory`: Whether filter out the duplicate query history.

`snowflakeDefaultRole`: This value represents the role of the snowflake database. Please note that you must define a role that has access to the SNOWFLAKE database and assign WAREHOUSE permission to this role.

## Backwards in code

<figure><img src="../../.gitbook/assets/185738467-b8485e3c-cbc4-4ceb-ab20-5e869908551b.gif" alt=""><figcaption></figcaption></figure>

