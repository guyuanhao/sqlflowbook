---
description: >-
  https://e.gitee.com/gudusoft/projects/151613/docs/655632/file/1546243?sub_id=5928451
---

# Job mode

SQLFlow Job mode is dedicated for handling large amounts of SQL Scripts or directly connecting to the target database server for the data linenage analysis. Config parameters for the analysis should be given when creating a new SQLFlow Job and the parameters cannot be changed once submitted.&#x20;

### Job type

There are two job types:

* Simple Job
* Regular Job

&#x20;

<figure><img src="../../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

Both Simple Job and Regular Job support reading large amounts of SQL files or analysis through DB directly. There are some differences between Simple Job and Regular Job.

#### Simple Job

* Possible to add some configs. Once submitted, the configs cannot be changed
* Result will be persisted in the file system as files

#### Regular Job

* Unable to set any data lineage configs
* Result will be in database
* Support whether incremental, possible to anaylze SQL scripts or database in batches
* Possible to do the Left Most analysis (Left Most: given a->b->c, show a->c )
* Possible to do the Upstream and Downstream analysis (given a->b->c, Upstream: a->b, Downstream: b->c)

### Summary Result

When using [SQLFlow Front UI](../../ui/), all data lineage will be returned if the number is less than 2,000. However, only database, schema, table, view data and the number of above DB units will be returned if the number is more than 2,000. No field data will be returned in the case and this is called **Summary result**.

User can request specific database, schema, table or view but result will be in Summary mode if the result number is more than 2,000.

There's a performance limitation in the frontend page rendering and moreover the graph will be complex to understand so we impose a restriction on the UI endpoint (/sqlflow/generation/sqlflow/graph). However, request to the [/sqlflow/generation/sqlflow](../../../api-docs/sqlflow-rest-api-reference/generation-interface/sqlflow-generation-sqlflow.md) for SQLFLow Rest Api doesn't have such limitation.