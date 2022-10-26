---
description: >-
  https://github.com/sqlparser/sqlflow_public/blob/master/sqlflow_guide_cn.md#schema
---

# Schema

<figure><img src="../../.gitbook/assets/Screenshot from 2022-10-25 23-53-00.png" alt=""><figcaption></figcaption></figure>

Visualize SQL schema by choosing any elements:

<figure><img src="../../.gitbook/assets/show_green_mode.gif" alt=""><figcaption></figcaption></figure>

There are three modes(the mode field in json) to display the response returned by graph AP which are represented by three different colors:

* global
* summay
* ignore record

<figure><img src="../../.gitbook/assets/Screenshot from 2022-10-26 00-10-45.png" alt=""><figcaption></figcaption></figure>

The green icons of ANALYTICS and ENTITY indicat that the mode is _global_;&#x20;

The black icons of DATAMART indicat that the mode is _summary_;&#x20;

The gray icons of other nodes indicat that the nodes are not visualized.

### View DDL(Data Definition Language)

<figure><img src="../../.gitbook/assets/show_DDL.gif" alt=""><figcaption></figcaption></figure>

### Schema Structure&#x20;

The tree structure in schema section may differ from the database types (check [here](../../sqlflow-ingester/understanding-the-format-of-exported-data.md) to find why it can be different). Same as the database, the tree strecture also has tree different cases.

#### Sample schema for Database who has the _database_ layer and the _schema_ layer (SQL Server for example)



#### Sample schema for Database who has the _database_ layer only (MYSQL for example)



#### Sample schema for Database who has the schema layer only (Oracle for example)
