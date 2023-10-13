# Exchange table partition

In Oracle, partitioning-related clauses for `ALTER TABLE` can be used with partitioned tables for repartitioning, to add, drop, discard, import, merge, and split partitions, and to perform partitioning maintenance.

The following SQL swaps data with the partition P1 in two tables:

```plsql
ALTER TABLE A1 EXCHANGE PARTITION(P1) WITH TABLE B2;
```

Result:

<figure><img src="../../.gitbook/assets/图片 (18).png" alt=""><figcaption></figcaption></figure>
