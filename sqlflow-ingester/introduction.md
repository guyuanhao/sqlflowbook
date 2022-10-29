---
description: https://e.gitee.com/gudusoft/docs/1006527/file/2767137?sub_id=5738180
---

# Introduction

### Why we need Sqlflow-Ingester?

Sqlflow actually supports two kinds of file as the input:

* SQL file, including comments. DDL file for an example, sql such as create table can be used as metadata.
* Json files which contain the database metadata

All other kinds of the input will be no longer supported and users shall convert the inputs to the above two formats. As a result, an out-of-box tool is needed to complete the conversion.

### Sqlflow-Ingester Basic

Sqlflow-Ingester is a tool helps you to extract metadata from various database. The metadata file can be later used by [dlineage tool](../introduction/java-library/) to generate data lineage.

Sqlflow-Ingester download address: [https://github.com/sqlparser/sqlflow\_public/releases](https://github.com/sqlparser/sqlflow\_public/releases)

Under linux:

```
./exporter.sh -host 127.0.0.1 -port 1521 -db orcl -user scott -pwd tiger -save /tmp/sqlflow-ingester -dbVendor dbvoracle
```

Under windows:

```
exporter.bat -host 127.0.0.1 -port 1521 -db orcl -user scott -pwd tiger -save c:\tmp\sqlflow-ingester -dbVendor dbvoracle
```

A metadata.json file will be generated after successfully export metadta from the database. Check [here](list-of-supported-dbvendors.md) for a full list of the supported databases.

