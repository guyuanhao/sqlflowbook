# Usages

## Visualize sqltext

Visualize the data lineage after analyzing the input SQL query.

* input: SQL text
* output: data lineage diagram

All necessary files are under this directory.

```
└── 1\
```

## **Visualize job**

Visualize the data lineage in a [SQLFlow Job](https://docs.gudusoft.com/introduction/getting-started/different-modes-in-gudu-sqlflow). The SQLFlow job must be already created.

* input: a SQLFlow job id, or leave it empty to view the latest job
* output: data lineage diagram

All necessary files are under this directory.

```
└── 2\
```

```javascript
$(async () => {
    const sqlflow = await SQLFlow.init({
        container: document.getElementById('demo-2'),
        width: 1000,
        height: 800,
        apiPrefix: 'http://101.43.8.206/api',
    });

    // view job detail by job id, or leave it empty to view the latest job
    await sqlflow.job.lineage.viewDetailById('b38273ec356d457bb98c6b3159c53be3');
});
```

## **Visualize job with hardcoded parameters**

Visualize the data lineage of a specified table or column in a SQLFlow job.

* input: a SQLFlow job id, or leave it empty to view the latest job
* input: database, schema, table, column.
  * If the column is omitted, return the data lineage for the specified table.
  * if the table and column are ommited, return the data lineage for the specified schema.
  * if the schema, table and column are ommited, return the data lineage for the specified database.
* output: data lineage diagram

All necessary files are under this directory.

```
└── 3\
```

```javascript
$(async () => {
    const sqlflow = await SQLFlow.init({
        container: document.getElementById('sqlflow'),
        width: 1000,
        height: 700,
        apiPrefix: 'http://101.43.8.206/api',
    });

    // view job detail by job id, or leave it empty to view the latest job
    await sqlflow.job.lineage.viewDetailById('b38273ec356d457bb98c6b3159c53be3');

    sqlflow.job.lineage.selectGraph({
        database: 'DWDB', //
        schema: 'DBO',
        table: '#TMP',
        column: 'NUMBER_OFOBJECTS',
    });
});
```

## **Visualize job with parameters**

Visualize the data lineage of a specified table or column in a SQLFlow job.

* input: a SQLFlow job id, or leave it empty to view the latest job
* input: database, schema, table, column.
  * If the column is omitted, return the data lineage for the specified table.
  * if the table and column are ommited, return the data lineage for the specified schema.
  * if the schema, table and column are ommited, return the data lineage for the specified database.
* output: data lineage diagram

All necessary files are under this directory.

```
└── 4\
```

## **Set data lineage options of SQL query**

Using the setting to control the output of data lineage of a SQL query.

All necessary files are under this directory.

```
└── 5\
```

## **Visualize an embedded json object in html page**

SQLFlow will visualize the json object which contains the data lineage information and will show the actionable diagram.

Since all layout data is included in the json file, the SQLFlow widget will draw the diagram and needn't to connect to the SQLFlow backend.

So this SQLFlow widget can work without the installation of the Gudu SQLFlow.

All necessary files are under this directory.

```
└── 6\
```

## **Visualize data lineage in a separate json file**

Read and visualize the data lineage in a json file. This json file should be accessable in the same server as the SQLFlow widget.

Since all layout data is included in the json file, the SQLFlow widget will draw the diagram and needn't to connect to the SQLFlow backend.

So, this SQLFlow widget can work without the installation of the Gudu SQLFlow.

All necessary files are under this directory.

```
└── 7\
```

## **Get error message**

Show how to get error message after processing input SQL qurey.

All necessary files are under this directory.

```
└── 8\
```

## **Event: add an event listener on field(column) click**

Add an event listener on field(column) click, so you can get detailed information about the field(column) that been clicked.

All necessary files are under this directory.

```
└── 9\
```

## **Access data lineage from url**

User can directly access the data lineage through an url by specifying the data lineage type, table and column.

> All data lineage comes from the default job at the Gudu SQLFlow backend. If no default job is set, lineage data will be retrieved from the latest job.

```
http://127.0.0.1/widget/12/?type=upstream&table=dbo.emp
http://127.0.0.1/widget/12/?type=upstream&table=dbo.emp&column=salary
```

* input
  * type: upstream or downstream
  * table
  * column: if column is omitted, return the lineage for table.

the table and column name in the url is case insensitive.

All necessary files are under this directory.

```
└── 12\
```

## **Visualize a csv file that includes lineage data**

The format of the csv

```csv
source_db,source_schema,source_table,source_column,target_db,target_schema,target_table,target_column,relation_type,effect_type
D1E9IQ1AE488E4,DBT_TESTS,STG_PAYMENTS,AMOUNT,DEFAULT,DEFAULT,RS-5,COUPON_AMOUNT,fdd,select
D1E9IQ1AE488E4,DBT_TESTS,STG_ORDERS,ORDER_ID,DEFAULT,DEFAULT,RS-5,ORDER_ID,fdd,select
D1E9IQ1AE488E4,DBT_TESTS,STG_ORDERS,STATUS,DEFAULT,DEFAULT,RS-5,STATUS,fdd,select
D1E9IQ1AE488E4,DBT_TESTS,STG_PAYMENTS,AMOUNT,DEFAULT,DEFAULT,RS-5,CREDIT_CARD_AMOUNT,fdd,select
D1E9IQ1AE488E4,DBT_TESTS,STG_PAYMENTS,AMOUNT,DEFAULT,DEFAULT,RS-5,GIFT_CARD_AMOUNT,fdd,select
D1E9IQ1AE488E4,DBT_TESTS,STG_ORDERS,ORDER_DATE,DEFAULT,DEFAULT,RS-5,ORDER_DATE,fdd,select
D1E9IQ1AE488E4,DBT_TESTS,STG_PAYMENTS,AMOUNT,DEFAULT,DEFAULT,RS-5,AMOUNT,fdd,select
D1E9IQ1AE488E4,DBT_TESTS,STG_ORDERS,CUSTOMER_ID,DEFAULT,DEFAULT,RS-5,CUSTOMER_ID,fdd,select
D1E9IQ1AE488E4,DBT_TESTS,STG_PAYMENTS,AMOUNT,DEFAULT,DEFAULT,RS-5,BANK_TRANSFER_AMOUNT,fdd,select
```

All necessary files are under this directory.

```
└── 13\
```

## **Visualize the lineage data using Vue**

The SQLFlow provides a Vue library to support Vue framework.

```
└── 14\
```

## **Event: add an event listener on table click**

Add an event listener on table click, so you can get detailed information about the table that been clicked.

```
└── 15\
```

