---
description: https://blog.sqlflow.cn/gudu-sqlflow-er-diagram/
---

# Convert SQL to E-R Diagram

Gudu SQLFlow is capable to convert **SQL to Entity-Relation(ER) Diagram** as well as to visualize the relations between tables and fields so that you can quickly understand the design model of the database and conduct efficient team communication.

## Two Sources of Visualization ER Model

*   From SQL Script

    SQLFlow can analyze Database creation SQL script and visualize the provided scripts which include statements such as `create table` or `alter table` into ER Model.&#x20;
*   From Database

    You can simply make SQLFlow connect to your database for the ER diagram. SQLFlow will automatically retrieve metadata from the database and generate the ER diagram.

## Three Ways to Visualize ER Model

Let's now take a look on how exactly to use GuduSQLFlow to do that.&#x20;

Gudu SQLFlow provides three ways:

### 1. Paste SQL Statements into the SQLText Editor

Directly Paste your SQL statements into the SQLText Editor

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

Click the icon of the ER model and you will have the correspond E-R Digram instantly.

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

### 2. Upload SQL files

Click `upload sql`

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

Choose `upload file` as the job source and choose the SQL type in the `dbvendor`. Upload file and create the [Job](../ui/job-management/).

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

Choose the job in the job list panel when it is complete.

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

Click `show ER diagram` in the schema explorer and check the result.

### 3. Connect to DB



