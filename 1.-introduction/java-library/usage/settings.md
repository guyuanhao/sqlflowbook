# Settings

**Simple mode** is enabled by default or in the cases when `/s` flag is added to the command:

```bash
java -jar gudusoft.dlineage.jar /t mssql /f path_to_sql_file /s
```

```
java -jar gudusoft.dlineage.jar /t mssql /f path_to_sql_file
```

In Simple mode, the intermediate results will not be displayed and only [fdd relationships](../../../2.-concepts/data-lineage/dataflow/relations-generated-by-sqlflow.md#the-meaning-of-the-letter-in-fdd-fdr) are present. The Simple mode is related to two options: `setSimpleShowTopSelectResultSet`, `setSimpleShowFunction` and `setSimpleShowUdfFunctionOnly`.

_**setSimpleShowTopSelectResultSet**_

whether to display the select result set on the top, default value is false.

_**setSimpleShowFunction**_

whether to  display function, default value is false.

_**setSimpleShowUdfFunctionOnly**_

whether to display only User Define Function, we also need to turn on `setSimpleShowFunction` as well so that functions are displayed.

```java
dlineage.getOption().setSimpleShowFunction(true); 
dlineage.getOption().setSimpleShowUdfFunctionOnly(true);
```

_dataflowAnalyzer_ is in Simple mode by default so there's no select result set on the top nethier no function displayed. Sqlflow UI will always have setSimpleShowTopSelectResultSet as true because the select query must be displayed on the top.

_dataflowAnalyzer_ has a function to deal with the dataflow in regular mode and customize the analysis type for the relations. The function can analysize [fdd](../../../2.-concepts/data-lineage/dataflow/relations-generated-by-sqlflow.md#the-meaning-of-the-letter-in-fdd-fdr) and [fdr](../../../2.-concepts/data-lineage/dataflow/relations-generated-by-sqlflow.md#the-meaning-of-the-letter-in-fdd-fdr) relations.

```java
Dataflow getSimpleDataflow(Dataflow instance, boolean simpleOutput, List <String> types)
```

* instance: dataflow in regular mode&#x20;
* simpleOutput: `false` when `showTopSelectResultSet` is set to `true`. `true` when `showTopSelectResultSet` is set to `false`.
* types: List of relation types, may include values as `fdd` or `fdr`. Will analysize `fdr` when the list contains `fdr`.

In Dlineage tool we can display temporary tables by adding `/withTemporaryTable` flag:

```shell
java -jar gudusoft.dlineage.jar /t mssql /f path_to_sql_file /withTemporaryTable
```

Please be aware that ignoring the temporary table starting with "`#`" in _sqlserver_ is a mandatory behavior, therefore it cannot be displayed even with the `/withTemporaryTable` flag.
