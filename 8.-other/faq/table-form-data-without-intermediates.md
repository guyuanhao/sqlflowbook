# Table Form Data Without  Intermediates

Let's say you have a data lineage like:

```
table1.column -> temp.column -> table2.column”
```

Instead of getting the temp table in the above result, you would prefer to have directly:&#x20;

```
table1.column -> table2.column
```

and if you would like to have the results under table form such as CSV, you can check the following two approaches:

## SQLFlow UI

## REST Call
