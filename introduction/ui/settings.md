---
description: >-
  https://github.com/sqlparser/sqlflow_public/blob/master/sqlflow_guide_cn.md#setting
---

# Settings

Input different request parameters to the graph API to get different results:

| Parameter                   | Acceptable values                                                                                                                                                                                                                    |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| showRelationType            | <p>If direct dataflow = true then it is fdd and we will show only direct dataflow.<br>If direct dataflow = true and indirect dataflow=true, then it is fdd,fddi,fdr,frd. We will show both direct dataflow and indrect dataflow.</p> |
| dataflowOfAggregateFunction | Whether take the parameters in the COUNT function as direct or indirect dataflow                                                                                                                                                     |
| ignoreRecordSet             | true or false                                                                                                                                                                                                                        |
| ignoreFunction              | true or false                                                                                                                                                                                                                        |
| showConstantTable           | true or false                                                                                                                                                                                                                        |
| showTransform               | true or false                                                                                                                                                                                                                        |

We can observe the changes on parameters when switching different modes:

<figure><img src="../../.gitbook/assets/185736267-6eefb036-f047-4a72-a95f-391847e5f145.gif" alt=""><figcaption></figcaption></figure>

### Configurable parameters when creating jobs or visualizing the SQL in SQL Editor

You will be able to set the config when creating data lineage with the SQL Edior as well as giving the configurable parameters under the `setting` section during the job creation.&#x20;

Customizing parameters when visualizing your SQL:

<figure><img src="../../.gitbook/assets/33_20221110205211.png" alt=""><figcaption></figcaption></figure>

Giving the configurable parameters under the `setting` section during the job creation:

<figure><img src="../../.gitbook/assets/Screenshot from 2022-11-01 21-08-42.png" alt=""><figcaption></figcaption></figure>

| Parameter                   | Possible Values | Description                                                                      |
| --------------------------- | --------------- | -------------------------------------------------------------------------------- |
| direct dataflow             | On/Off          | Whether show direct dataflow or not.                                             |
| indirect dataflow           | On/Off          | Whether show indirect dataflow or not.                                           |
| dataflow of count function  | direct/indirect | Whether take the parameters in the COUNT function as direct or indirect dataflow |
| show intermediate recordset | On/Off          | Show intermediate recordset or not.                                              |
| show function               | On/Off          | Show `function` or not                                                           |
| show transform              | On/Off          | Show `transform` or not                                                          |
| show constant               | On/Off          | show `constant` or not                                                           |

Take the following sql as example:

```sql
SELECT count(sal) totalNum, sum(sal) totalSal 
FROM   scott.emp 
```

When we set all values as `On` and `direct` as the value in _dataflow of count function_ when creating the job/visualizing the SQL, we will get following data lineage

<figure><img src="../../.gitbook/assets/Screenshot from 2022-11-10 20-40-51.png" alt=""><figcaption></figcaption></figure>

### Show function

<figure><img src="../../.gitbook/assets/185736347-1ce8fbf9-b66e-45e8-af75-137b746bc31d.gif" alt=""><figcaption></figcaption></figure>

### Show transform

<figure><img src="../../.gitbook/assets/185736610-6fba47eb-9dba-42cc-9f00-5af3ad22563f.gif" alt=""><figcaption></figcaption></figure>

### Export the graph

<figure><img src="../../.gitbook/assets/185734305-70c24757-c59c-40b4-b235-a79a214b7472.png" alt=""><figcaption></figcaption></figure>
