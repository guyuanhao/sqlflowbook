# Job Sources

Job source can be from one of the following sources:

### Upload file

`upload file`: The data lineage will be generated from the sql meta file you upload(DDL file for an example). Check our [Ingester tool](broken-reference) if you want use this way but don't have compatible sql metadata file.

<figure><img src="../../../.gitbook/assets/Screenshot from 2022-11-04 21-56-01.png" alt=""><figcaption></figcaption></figure>

### From database

`from database`: SQLFLow is able to read information directly from the database server and analyze the data lineage. You need to give the connection paramters in this mode.

### Upload file + database metadata

`upload file + database metadata`: Use the above two methods to create the Job together. You may need to use this mode when your data are distracted in different systems.

### Dbt

`dbt`: Read from dbt, the manifest.json and the catalog.json will be required.

### RedShift log

`redshift log`: Read from your redshift log.

### Snowflake query history

`snowflake query history`: Read from your snowflake query history.&#x20;



<figure><img src="../../../.gitbook/assets/Screenshot from 2022-11-03 00-30-54.png" alt=""><figcaption></figcaption></figure>

`enableQueryHistory`: Fetch SQL queries from the query history if set to `true`.

`blockOfTimeInMinutes`: When `enableQueryHistory`is set to true, the interval at which the SQL query was extracted in the query History.

`queryHistorySqlType`: Specify what's kind of SQL statements need to be sent to the SQLFlow for furhter processing after fetch the queries from the Snowflake query history. If `queryHistorySqlType` is specified, will only pickup those SQL statement type and send it the SQLFlow for furhter processing. This can be useful when you only need to discover lineage from a specific type of SQL statements. If `queryHistorySqlType` is empty, all queries fetched from the query history will be sent to the SQLFlow server.

`excludedHistoryDbsSchemas`: List of databases and schemas to exclude from extraction, separated by commas `database1.schema1,database2`.

`duplicateQueryHistory`: Whether filter out the duplicate query history.

`snowflakeDefaultRole`: This value represents the role of the snowflake database. Please note that you must define a role that has access to the SNOWFLAKE database and assign WAREHOUSE permission to this role.



<figure><img src="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FHPaNIbjpxIoccnaNkyJQ%2Fuploads%2FnX8sMhZRLCVRfX9zdFtN%2FScreenshot%20from%202022-11-01%2021-01-59.png?alt=media&#x26;token=e8f65227-8a3e-4243-8794-f90f3b80343b" alt=""><figcaption></figcaption></figure>

#### &#x20;  <a href="#default-server-database-schema" id="default-server-database-schema"></a>
