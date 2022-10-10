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

<figure><img src="../../../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

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
