# Snowflake table function lineage detection

SQLFlow is able to detect the Snowflake table function lineage.

Check the following sample code:

```sql
CREATE TABLE T1
(
C1 INT,
C2 VARIANT
);

CREATE TEMPORARY TABLE T_TMP AS
	(SELECT C1,
		-- META_DATA,
		Parse_json(META_DATA.value) AS C2_ID
		FROM T1 AS table_alias
		cross join TABLE(Flatten(C2)) AS META_DATA
	) ;

INSERT INTO T2
(C1,
-- META_DATA,
C2_ID)
(SELECT C1,
-- META_DATA,
C2_ID
FROM T_TMP);
```

With SQLFlow, the `T1.C2 -> T_TMP.C2_ID -> T2.C2_ID` lineage is properly generated.

<figure><img src="../../.gitbook/assets/Screenshot from 2024-01-08 12-21-31.png" alt=""><figcaption></figcaption></figure>
