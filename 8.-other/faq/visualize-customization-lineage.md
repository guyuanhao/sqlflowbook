# Visualize Customization Lineage

SQLFlow enables the customization of the data lineage in case users need to build their own visual representaiton of the query making it more comprehensible for non DBA people.

Let's take a simple query as an example:

```sql
TABLE1.A -> TABLE2.B
```

### &#x20;Get Lineage Model

All SQLFlow lineages can be represented under the lineage model structure. It can either be in Json format or in XML format. Please refer to [this page](../../7.-reference/lineage-model/) to read the details information for the lineage mode.&#x20;

There are several ways to retrieve the SQLFlow lineage mode:&#x20;

1. Invoking REST APIs,  [/sqlflow/graph](https://docs.gudusoft.com/3.-api-docs/sqlflow-rest-api-reference/generation-interface/sqlflow-graph) for example will give the lineage model.
2. Using GSP [https://docs.gudusoft.com/1.-introduction/java-library](https://docs.gudusoft.com/1.-introduction/java-library)
3. DIrectly copy the lineage model value from SQLFlow Web\
