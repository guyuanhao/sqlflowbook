---
description: >-
  https://github.com/sqlparser/sqlflow_public/blob/master/sqlflow_guide_cn.md#setting
---

# Settings

Input different request parameters to the graph API to get different results:

| Parameter                   | Acceptable values                                                                                                                      |
| --------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| showRelationType            | <p>if direct dataflow = true then it is fdd;<br>if direct dataflow = true and indirect dataflow=true, then it is fdd,fddi,fdr,frd;</p> |
| dataflowOfAggregateFunction | direct or indirect                                                                                                                     |
| ignoreRecordSet             | true or false                                                                                                                          |
| ignoreFunction              | true or false                                                                                                                          |
| showConstantTable           | true or false                                                                                                                          |
| showTransform               | true or false                                                                                                                          |

We can observe the changes on parameters when switching different modes:

<figure><img src="../../.gitbook/assets/185736267-6eefb036-f047-4a72-a95f-391847e5f145.gif" alt=""><figcaption></figcaption></figure>

### Configurable parameters when creating jobs

You can give the configurable parameters under the `setting` section during the job creation. Check [here](../getting-started/different-modes-in-gudu-sqlflow/job-mode.md#simple-job) to get more details for these parameters.

<figure><img src="../../.gitbook/assets/Screenshot from 2022-11-01 21-08-42.png" alt=""><figcaption></figcaption></figure>

| Parameter                   | Possible Values | Description                                                                       |
| --------------------------- | --------------- | --------------------------------------------------------------------------------- |
| direct dataflow             | On/Off          | Whether explain the aggregate function(COUNT for an example) as a direct dataflow |
| indirect dataflow           |                 |                                                                                   |
| dataflow of count function  |                 |                                                                                   |
| show intermediate recordset |                 |                                                                                   |
| show function               |                 |                                                                                   |
| show transform              |                 |                                                                                   |
| show constant               |                 |                                                                                   |

### Show function

<figure><img src="../../.gitbook/assets/185736347-1ce8fbf9-b66e-45e8-af75-137b746bc31d.gif" alt=""><figcaption></figcaption></figure>

### Show transform

<figure><img src="../../.gitbook/assets/185736610-6fba47eb-9dba-42cc-9f00-5af3ad22563f.gif" alt=""><figcaption></figcaption></figure>

### Export the graph

<figure><img src="../../.gitbook/assets/185734305-70c24757-c59c-40b4-b235-a79a214b7472.png" alt=""><figcaption></figcaption></figure>
