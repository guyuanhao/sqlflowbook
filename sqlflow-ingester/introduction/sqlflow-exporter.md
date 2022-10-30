---
description: https://e.gitee.com/gudusoft/docs/1006527/file/2767137?sub_id=5768619
---

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

`-dbVendor`: Database type, Check [here](../list-of-supported-dbvendors.md) for a full list of the supported databases. Use colon to split dbVendor and version if specific version is required. (\<dbVendor>:\<version>, such as dbvmysql:5.7) \
`-host`: Database host name (ip address or domain name) \
`-port`: Port number\
`-db`: Database name\
`-user`: User name \
`-pwd`: User password \
\-save: Destination folder path where we put the exported metadata json file. The exported file will be in name as `metadata.json`. \
`-extractedDbsSchemas`: Export metadata under the specific schema. Use comma to split if multiple schema required (such as \<schema1>,\<schema2>). We can use this flag to [improve the export performance](sqlflow-exporter.md#improve-export-performance).\
`-excludedDbsSchemas`:  Exclude metadata under the specific schema during the export. Use comma to split if multiple schema required (such as \<schema1>,\<schema2>). We can use this flag to [improve the export performance](sqlflow-exporter.md#improve-export-performance).\
`-extractedViews`: Export metadata under the specific view. Use comma to split if multiple views required (such as \<view1>,\<view2>). We can use this flag to [improve the export performance](sqlflow-exporter.md#improve-export-performance). \
`-merge`: Merge the metadata results which are exported in different process. Use comma to split files to merge. Check [here](sqlflow-exporter.md#improve-export-performance) for more details.

### Improve Export Performance

Time consumed during the export from database could be very long if the data volume is huge. Following actions are made to improve the Ingester export performance:

* JDBC `fetchsize` is set to 2000 for table and view. For sql of view and process the `fetchsize` is set to 500. (check this oracle doc for what is jdbc `fetchsize`: [https://docs.oracle.com/middleware/1212/toplink/TLJPA/q\_jdbc\_fetch\_size.htm#TLJPA647](https://docs.oracle.com/middleware/1212/toplink/TLJPA/q\_jdbc\_fetch\_size.htm#TLJPA647))
* Parameters `extractedDbsSchemas`, `excludedDbsSchemas` and `extractedViews` are improved for oracle and postgresql. A plan has already been made to improve the implementation of these parameters for other databases.

`-merge` can be used to merge the metadata results. Use comma to split files to merge. All files under the folder will be merged if the given value is the folder path.

```bash
exporter.bat -dbVendor dbvpostgresql -extractedDbsSchemas kingland.dbt%,kingland.pub%  -host 115.159.225.38 -port 5432 -db kingland -user bigking -pwd Cat_*** -save D:/out/1.json
exporter.bat -dbVendor dbvpostgresql -extractedDbsSchemas kingland.sqlflow  -host 115.159.225.38 -port 5432 -db kingland -user bigking -pwd Cat_*** -save D:/out/2.json
exporter.bat -merge  D:/out/1.json,D:/out/2.json    -save D:/out/merge.json
or
exporter.bat -merge  D:/out/   -save D:/out/merge.json
```
