# Widget API Reference

## **vendor.set(value: Vendor)**

set the type of database vendor, Vendor is an enum type.

```ts
type Vendor =
    | 'athena'
    | 'azuresql'
    | 'bigquery'
    | 'couchbase'
    | 'db2'
    | 'greenplum'
    | 'hana'
    | 'hive'
    | 'impala'
    | 'informix'
    | 'mdx'
    | 'mysql'
    | 'netezza'
    | 'openedge'
    | 'oracle'
    | 'postgresql'
    | 'presto'
    | 'redshift'
    | 'snowflake'
    | 'sparksql'
    | 'mssql'
    | 'sybase'
    | 'teradata'
    | 'vertica';
```

## **vendor.get(): Vendor**

return the current database vendor.

## **sqltext.set(value: string): void**

set the input sql query that need to be processed.

## **sqltext.get(): string**

Return the current SQL query text.

## **visualize(): Promise\<void>**

Show the diagram related to current input SQL.

## **job.lineage.viewDetailById(jobId?: string): Promise\<void>**

Show the diagram of a specific job. if the job id is omitted, show the diagram of the top job, if no top job is found, show the diagram of latest job.

## **job.lineage.selectGraph(options: { database?: string; schema?: string; table?: string; column?: string;}): Promise\<void>**

Show the lineage diagram of a specific table/column. `job.lineage.viewDetailById` must be called first before calling this function, and this function can be called multiple times to return diagram for different table/columns.

## **addEventListener(event: Event, callback: Callback): void**

Add an event listner.

Callback：(data) => any

### **Event：'onFieldClick'**

This event fired when the column in the diagram is clicked.

data：

| Attribute | Type                | Comment |
| --------- | ------------------- | ------- |
| database  | string \| undefined | name    |
| schema    | string \| undefined | name    |
| table     | string \| undefined | name    |
| column    | string              | name    |

## **removeEventListener(event: Event, callback: Callback): void**

Remove a event listner.

## **removeAllEventListener(): void**

Remove all event listners.
