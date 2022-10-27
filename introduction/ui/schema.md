---
description: >-
  https://github.com/sqlparser/sqlflow_public/blob/master/sqlflow_guide_cn.md#schema
---

# Schema

### Schema Explorer Basic

<figure><img src="../../.gitbook/assets/Screenshot from 2022-10-25 23-53-00.png" alt=""><figcaption></figcaption></figure>

Visualize SQL schema by choosing any elements

<figure><img src="../../.gitbook/assets/show_green_mode.gif" alt=""><figcaption></figcaption></figure>

There are three modes(the mode field in json) to display the response returned by graph AP which are represented by three different colors:

* global
* summay
* ignore record

<figure><img src="../../.gitbook/assets/Screenshot from 2022-10-26 00-10-45.png" alt=""><figcaption></figcaption></figure>

The green icons of ANALYTICS and ENTITY indicat that the mode is _global_;&#x20;

The black icons of DATAMART indicat that the mode is _summary_;&#x20;

The gray icons of other nodes indicat that the nodes are not visualized.

### Visualization Control

You may find following elements when right click on the database/schema/table/column elements in the schema explorer:

<figure><img src="../../.gitbook/assets/Screenshot from 2022-10-28 00-47-20.png" alt=""><figcaption></figcaption></figure>

_`visualize`_: Generate the selected db elements(could be a database/schema/table/column etc) data lineage.

<figure><img src="../../.gitbook/assets/Screenshot from 2022-10-28 00-52-43.png" alt=""><figcaption></figcaption></figure>

In above screenshot only the selected _`customer_id`_ column related data lineage is displayed.

_`visualize with cloumns`_: Generate the selected db elements(could be a database/schema/table etc) data lineage with column details.

<figure><img src="../../.gitbook/assets/Screenshot from 2022-10-28 01-01-50.png" alt=""><figcaption></figcaption></figure>

_`to left most`_: Generate the selected db elements(could be a database/schema/table/column etc) data lineage without the record set.

<figure><img src="../../.gitbook/assets/Screenshot from 2022-10-28 01-08-06.png" alt=""><figcaption></figcaption></figure>

_`to left most with columns`_: Generate the selected db elements(could be a database/schema/table/column etc) data lineage with the column details but without the record set.

<figure><img src="../../.gitbook/assets/Screenshot from 2022-10-28 01-10-25.png" alt=""><figcaption></figcaption></figure>

_`copy`_: copy the element name so that we can quickly search the elements with the similar name.

### View DDL(Data Definition Language)

<figure><img src="../../.gitbook/assets/show_DDL.gif" alt=""><figcaption></figcaption></figure>

### Different Schema Structures&#x20;

The tree structure in schema section may differ from the database types (check [here](../../sqlflow-ingester/understanding-the-format-of-exported-data.md) to find why it can be different). Same as the database, the tree strecture also has tree different cases.

#### Sample schema for Database who has the _database_ layer and the _schema_ layer (SQL Server for example)

<figure><img src="../../.gitbook/assets/Screenshot from 2022-10-27 00-27-54.png" alt=""><figcaption></figcaption></figure>

For MSSQL, we have Database layer as well as Schema layer. The two layers will be both displayed on the schema UI.

#### Sample schema for Database who has the _database_ layer only (MYSQL for example)

<figure><img src="../../.gitbook/assets/Screenshot from 2022-10-27 00-30-27.png" alt=""><figcaption></figcaption></figure>

For MYSQL, we have Database layer but we do not have Schema layer. Schema is same as Database for MYSQL. Only Database layer is displayed on the schema UI.

#### Sample schema for Database who has the schema layer only (Oracle for example)

<figure><img src="../../.gitbook/assets/Screenshot from 2022-10-27 00-32-45.png" alt=""><figcaption></figcaption></figure>

For ORACLE, we have Schema layer but there is no Database layer for ORACLE. Only Schema layer is displayed on the schema UI.
