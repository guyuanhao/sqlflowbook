# Summary mode

When using [SQLFlow Front UI](../../ui/), all data lineage will be returned if the number is less than 2,000. However, only database, schema, table, view data and the number of above DB units will be returned if the number is more than 2,000. No field data will be returned in the case and this is called **Summary mode**.

User can request specific database, schema, table or view but result will be in Summary mode if the result number is more than 2,000.

### Why Summary mode?

There's a performance limitation in the frontend page rendering and moreover the graph will be complex to understand so we impose a restriction on the UI endpoint (/sqlflow/generation/sqlflow/graph). However, request to the [/sqlflow/generation/sqlflow](../../../api-docs/sqlflow-rest-api-reference/generation-interface/sqlflow-generation-sqlflow.md) for SQLFLow Rest Api doesn't have such limit.
