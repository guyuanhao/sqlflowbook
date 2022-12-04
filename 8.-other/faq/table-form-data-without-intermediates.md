# Table Form Data Without  Intermediates

Let's say you have a data lineage like:

```
table1.column -> temp.column -> table2.column”
```

Instead of getting the temp table in the above result, you would prefer to have directly:&#x20;

```
table1.column -> table2.column
```

and if you would like to have the results under table form such as CSV, you can check the following two approaches.&#x20;

Let's consider this SQL:

```sql
INSERT INTO deptsal
            (dept_no,
             dept_name,
             salary)
SELECT d.deptno,
       d.dname,
       SUM(e.sal + Nvl(e.comm, 0)) AS sal
FROM   dept d
       left join (SELECT *
                  FROM   emp
                  WHERE  hiredate > DATE '1980-01-01') e
              ON e.deptno = d.deptno
GROUP  BY d.deptno,
          d.dname; 
```

## SQLFlow UI

The initial status of the lineage contains temporary tables

<figure><img src="../../.gitbook/assets/111_20221204172525.png" alt=""><figcaption></figcaption></figure>



## REST Call
