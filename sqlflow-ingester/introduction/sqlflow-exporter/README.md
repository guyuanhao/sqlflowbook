# SQLFlow-Exporter

SQLFlow-exporter is the main functionality of the SQLFlow-Ingester. It is used to getting the metadata from different databases.

### SQLFlow-Exporter Usage

Under linux:

```
./exporter.sh -host 127.0.0.1 -port 1521 -db orcl -user scott -pwd tiger -save /tmp/sqlflow-ingester -dbVendor dbvoracle
```

Under windows:

```
exporter.bat -host 127.0.0.1 -port 1521 -db orcl -user scott -pwd tiger -save c:\tmp\sqlflow-ingester -dbVendor dbvoracle
```

Or you can directly execute the .jar package, the jar packages are under the `./lib` folder:&#x20;

```
java -jar sqlflow-exporter-1.0.jar  -host 106.54.134.160 -port 1521 -db orcl -user bigking -pwd Cat_12345 -save d:/ -dbVendor dbvoracle
```

A metadata.json file will be generated after successfully export metadta from the database.&#x20;

Example for the success output:&#x20;

```
exporter metadata success: <-save>/metadata.json
```

### Parameters

\-dbVendor: Database type, Check [here](../../list-of-supported-dbvendors.md) for a full list of the supported databases. Use colon to split dbVendor and version if specific version is required. (\<dbVendor>:\<version>, such as dbvmysql:5.7) \
\-host: Database host name (ip address or domain name) \
\-port: Port number\
\-db: Database name\
\-user: User name \
\-pwd: User password \
\-save: Destination folder path where we put the exported metadata json file. The exported file will be in name as `metadata.json`. \
\-extractedDbsSchemas: Export metadata under the specific schema. Use comma to split if multiple schema required (such as \<schema1>,\<schema2>). We can use this flag to [improve the export performance](improve-export-performance.md).\
\-excludedDbsSchemas:  Exclude metadata under the specific schema during the export. Use comma to split if multiple schema required (such as \<schema1>,\<schema2>). We can use this flag to [improve the export performance](improve-export-performance.md).\
\-extractedViews: Export metadata under the specific view. Use comma to split if multiple view required (such as \<view1>,\<view2>). We can use this flag to [improve the export performance](improve-export-performance.md).&#x20;
