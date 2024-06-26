# Resolve the ambiguous columns in SQL query

Given the following SQL:

```sql
select ename
from emp, dept
where emp.deptid = dept.id
```

Column `ename` in the first line is not qualified by table name `emp` and how can we know which table this column belongs to?

#### Solution 1:  Using table DDL

There are two ways to use the table DDL to eliminate the ambiguity.

* The first way is to put the DDL before the above SQL statement in the same SQL file and the column `ename` will be linked to the table `emp` correctly.

```sql
create table emp(
	id int,
	ename char(50),
	deptid int
);

create table dept(
	id int,
	dname char(50)
);
```

* The second way is putting the DDL file under the same folder as the sql files and using the `/d` flag to explicitly give the path of the DDL file directory.

```
java -jar gudusoft.dlineage.jar /t oracle /d path_to_sql_file_directory
```

#### Solution 2: Using metadata exported from database

Since dlineage v2.2.0 (2022/7/21), This dlineage tool supports `/env` parameter to accept a metadata json file which includes the metadata exported from a database.

By providing metadata.json that includes the metadata, column `ename` should be linked to the table `emp` correctly.

You can use `/env` to specify a metadata.json like this:

```
java -jar gudusoft.dlineage.jar /t oracle /f path_to_sql_file /env metadata.json
```

You can always extract metadata from the database use the [sqlflow-ingester](https://github.com/sqlparser/sqlflow\_public/releases) tool.
