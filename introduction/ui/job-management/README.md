---
description: >-
  https://github.com/sqlparser/sqlflow_public/blob/master/sqlflow_guide_cn.md#job-list
---

# Job Management

## Job list

<figure><img src="../../../.gitbook/assets/185734108-5dc282df-0b49-4061-af2d-c9fa21ab885a.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/Screenshot from 2022-11-06 16-29-30.png" alt=""><figcaption></figcaption></figure>

Note that `Lineage Overview` can not be applied on[ regular job](../../getting-started/different-modes-in-gudu-sqlflow/job-mode.md#regular-job) cause process data are needed but we don't have that in the database.

## Create a job

<figure><img src="../../../.gitbook/assets/185737736-814ae584-ab72-4be6-a4f6-6393607d385f.gif" alt=""><figcaption></figcaption></figure>

### Click the Job Creation button in the Job List Section

<figure><img src="../../../.gitbook/assets/20221101205559.png" alt=""><figcaption></figcaption></figure>

### Enter the Job creation parameters&#x20;

<figure><img src="../../../.gitbook/assets/Screenshot from 2022-11-01 21-00-58.png" alt=""><figcaption></figcaption></figure>

### Job sources

{% content-ref url="job-sources.md" %}
[job-sources.md](job-sources.md)
{% endcontent-ref %}

### Default server/database/schema

Give the default value for server/database/schema when there's no related metadata to the database units(such as table,view etc...). If the default values are given here, will use the given values. Otherwise will use `default` as the value for server/database/schema if the default server/database/schema is not set.

<figure><img src="../../../.gitbook/assets/Screenshot from 2022-11-01 21-22-38.png" alt=""><figcaption></figcaption></figure>

### Job Type

Choose the Job type when creating the Job. Read more on the [Job type](../../getting-started/different-modes-in-gudu-sqlflow/job-mode.md).

<figure><img src="../../../.gitbook/assets/Screenshot from 2022-11-01 21-04-21.png" alt=""><figcaption></figcaption></figure>

### Advanced

Customized the extraction/exclusion content under the `advanced` section

<figure><img src="../../../.gitbook/assets/Screenshot from 2022-11-01 21-06-07.png" alt=""><figcaption></figcaption></figure>

### Configurable parameters

You can give the configurable parameters under the `setting` section. Check [here](../settings.md#configurable-parameters-when-creating-jobs-or-visualizing-the-sql-in-sql-editor) to get more details about these parameters.

<figure><img src="../../../.gitbook/assets/Screenshot from 2022-11-01 21-08-42.png" alt=""><figcaption></figcaption></figure>

## Backwards in code

<figure><img src="../../../.gitbook/assets/185738467-b8485e3c-cbc4-4ceb-ab20-5e869908551b.gif" alt=""><figcaption></figcaption></figure>

