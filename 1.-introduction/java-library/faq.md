# FAQ

## Q: How to set default database and schema in DataFlowAnalyzer?

```java
DataFlowAnalyzer dlineage = new DataFlowAnalyzer(sql, vendor, simpleMode);
dlineage.getOption().setDefaultDatabase("PRD");
dlineage.getOption().setDefaultSchema("apps");
```

From DataFlowAnalyzer instance, getting the `Option` field in the instance, use `setDefaultDatabase` and `setDefaultSchema` methods to set default database and schema.

## Q: Relationship is parsed but procedureId is null

```java
option.setTraceProcedure(true);
```

To trace the procedure in the relationship, the flag traceProcedure needs to be open. The default value of the flag is false.
