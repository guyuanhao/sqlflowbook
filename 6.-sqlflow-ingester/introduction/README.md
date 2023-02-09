---
description: https://e.gitee.com/gudusoft/docs/1006527/file/2767137?sub_id=5738180
---

# Introduction

### Why we need SQLFlow-Ingester?

SQLFlow supports two kinds of file as the input:

* SQL file, including comments. DDL file for an example, sql such as create table can be used as metadata.
* Json files which contain the database metadata

All other kinds of the input will be no longer supported and users shall convert the inputs to the above two formats. As a result, an out-of-box tool is needed to complete the conversion.

### SQLFlow-Ingester Basic

SQLFlow-Ingester is a tool helps you to extract metadata from various database. The metadata file can be later used by [dlineage tool](../../1.-introduction/java-library/) to generate data lineage.

SQLFlow-Ingester download address: [https://github.com/sqlparser/sqlflow\_public/releases](https://github.com/sqlparser/sqlflow\_public/releases)

SQLFlow-Ingester has three different parts:

* sqlflow-exporter: getting metadata from database
* sqlflow-extractor: processing raw data files such as log files, various script files (from which SQL statements and metadata to be processed are extracted), CSV files containing SQL statements, etc.
* sqlflow-submitter: submitting sql and metadata to the sqlflow server, creating jobs, generating data lineage, and having the results in the UI.

Read more details for the above Ingester components:

{% content-ref url="sqlflow-exporter.md" %}
[sqlflow-exporter.md](sqlflow-exporter.md)
{% endcontent-ref %}

{% content-ref url="sqlflow-extractor.md" %}
[sqlflow-extractor.md](sqlflow-extractor.md)
{% endcontent-ref %}

{% content-ref url="sqlflow-submitter.md" %}
[sqlflow-submitter.md](sqlflow-submitter.md)
{% endcontent-ref %}
