---
description: >-
  https://e.gitee.com/gudusoft/projects/151613/docs/655632/file/1546243?sub_id=5928451
---

# Query mode

Query mode can be used to analyze single SQL script or multiple SQL instructions. Directly give your SQL script to our [online frontend SQLFlow editor](https://sqlflow.gudusoft.com/#/) and get your data lineage by simply clicking on `Visualize` button.&#x20;

### How it works?

In query mode, user makes request to [/sqlflow/generation/sqlflow](../../../api-docs/sqlflow-rest-api-reference/generation-interface/sqlflow-generation-sqlflow.md) without giving `jobId` and our backend server analyzes the given SQL directly.&#x20;

### Features of Query mode

Query mode is ideal to handle lightweight SQL(no more than 500KB) and get the detailed response with which you can know how SQLFlow works and learn usages of SQLFlow functions. Query mode iss

* All paramaters are supported. Data lineage results are returned immediately after sending the request.
* Support the smallest granularity analysis. Possible to give [Functions in data lineage](../../../concepts/data-lineage/aggregate-function-and-dataflow.md), I[ndirect data lineage](../../../concepts/data-lineage/indirect-dataflow.md) and Constant in data lineage.
* Query mode is unable to connect database server to get the data lineage.
* Query mode cannot analyze multiple SQL files in the same time.
