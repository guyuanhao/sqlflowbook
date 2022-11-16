# Oracle

This page gives a sample metadata for **Oracle**.

## Sample

```json
{
    "createTime": "2022-11-07 23:30:12",
    "createdBy": "sqlflow-ingester v1.1.7",
    "physicalInstance": "106.54.xx.xx",
    "servers": [
        {
            "dbLinks": [],
            "dbVendor": "dbvoracle",
            "name": "106.54.xx.xx",
            "queries": [
                {
                    "database": "",
                    "groupName": "\"SH\".\"FWEEK_PSCAT_SALES_MV\"",
                    "name": "FWEEK_PSCAT_SALES_MV",
                    "schema": "SH",
                    "sourceCode": "CREATE MATERIALIZED VIEW \"SH\".\"FWEEK_PSCAT_SALES_MV\" as SELECT   t.week_ending_day\n  ,        p.prod_subcategory\n  ,        sum(s.amount_sold) AS dollars\n  ,        s.channel_id\n  ,        s.promo_id\n  FROM     sales s\n  ,        times t\n  ,        products p\n  WHERE    s.time_id = t.time_id\n  AND      s.prod_id = p.prod_id\n  GROUP BY t.week_ending_day\n  ,        p.prod_subcategory\n  ,        s.channel_id\n  ,        s.promo_id",
                    "type": "materialized view"
                }
            ],
            "schemas": [
                {
                    "functions": [
                        {
                            "arguments": [
                                {
                                    "dataType": "VARRAY",
                                    "name": "P_PHONELIST"
                                }
                            ],
                            "database": "",
                            "name": "GET_PHONE_NUMBER_F",
                            "schema": "\"OE\""
                        }
                    ],
                    "name": "\"OE\"",
                    "sequences": [
                        {
                            "database": "",
                            "incrementBy": "1",
                            "name": "ORDERS_SEQ",
                            "schema": "\"OE\""
                        }
                    ],
                    "synonyms": [
                        {
                            "database": "",
                            "name": "COUNTRIES",
                            "schema": "\"OE\"",
                            "sourceDbLinkName": "",
                            "sourceName": "COUNTRIES",
                            "sourceSchema": "HR"
                        },
                        {
                            "database": "",
                            "name": "LOCATIONS",
                            "schema": "\"OE\"",
                            "sourceDbLinkName": "",
                            "sourceName": "LOCATIONS",
                            "sourceSchema": "HR"
                        },
                        {
                            "database": "",
                            "name": "DEPARTMENTS",
                            "schema": "\"OE\"",
                            "sourceDbLinkName": "",
                            "sourceName": "DEPARTMENTS",
                            "sourceSchema": "HR"
                        },
                        {
                            "database": "",
                            "name": "JOBS",
                            "schema": "\"OE\"",
                            "sourceDbLinkName": "",
                            "sourceName": "JOBS",
                            "sourceSchema": "HR"
                        },
                        {
                            "database": "",
                            "name": "EMPLOYEES",
                            "schema": "\"OE\"",
                            "sourceDbLinkName": "",
                            "sourceName": "EMPLOYEES",
                            "sourceSchema": "HR"
                        },
                        {
                            "database": "",
                            "name": "JOB_HISTORY",
                            "schema": "\"OE\"",
                            "sourceDbLinkName": "",
                            "sourceName": "JOB_HISTORY",
                            "sourceSchema": "HR"
                        }
                    ],
                    "tables": [
                        {
                            "columns": [
                                {
                                    "comment": "",
                                    "dataType": "VARCHAR2(50 byte)",
                                    "name": "CATEGORY_NAME"
                                },
                                {
                                    "comment": "",
                                    "dataType": "VARCHAR2(1000 byte)",
                                    "name": "CATEGORY_DESCRIPTION"
                                },
                                {
                                    "comment": "",
                                    "dataType": "NUMBER(2)",
                                    "name": "CATEGORY_ID"
                                },
                                {
                                    "comment": "",
                                    "dataType": "NUMBER(2)",
                                    "name": "PARENT_CATEGORY_ID"
                                }
                            ],
                            "databaseName": "",
                            "name": "CATEGORIES_TAB",
                            "schemaName": "\"OE\"",
                            "type": "table"
                        },
                        {
                            "columns": [
                                {
                                    "comment": "Part of concatenated primary key, references product_information.product_id.",
                                    "dataType": "NUMBER(6)",
                                    "name": "PRODUCT_ID"
                                },
                                {
                                    "comment": "Part of concatenated primary key, references warehouses.warehouse_id.",
                                    "dataType": "NUMBER(3)",
                                    "name": "WAREHOUSE_ID"
                                },
                                {
                                    "comment": "",
                                    "dataType": "NUMBER(8)",
                                    "name": "QUANTITY_ON_HAND"
                                }
                            ],
                            "databaseName": "",
                            "name": "INVENTORIES",
                            "schemaName": "\"OE\"",
                            "type": "table"
                        },
                        {
                            "columns": [
                                {
                                    "comment": "PRIMARY KEY column.",
                                    "dataType": "NUMBER(12)",
                                    "name": "ORDER_ID"
                                },
                                {
                                    "comment": "TIMESTAMP WITH LOCAL TIME ZONE column, NOT NULL constraint.",
                                    "dataType": "TIMESTAMP(6) WITH LOCAL TIME ZONE(38,6)",
                                    "name": "ORDER_DATE"
                                },
                                {
                                    "comment": "CHECK constraint.",
                                    "dataType": "VARCHAR2(8 byte)",
                                    "name": "ORDER_MODE"
                                },
                                {
                                    "comment": "",
                                    "dataType": "NUMBER(6)",
                                    "name": "CUSTOMER_ID"
                                },
                                {
                                    "comment": "0: Not fully entered, 1: Entered, 2: Canceled - bad credit, -\n3: Canceled - by customer, 4: Shipped - whole order, -\n5: Shipped - replacement items, 6: Shipped - backlog on items, -\n7: Shipped - special delivery, 8: Shipped - billed, 9: Shipped - payment plan,-\n10: Shipped - paid",
                                    "dataType": "NUMBER(2)",
                                    "name": "ORDER_STATUS"
                                },
                                {
                                    "comment": "CHECK constraint.",
                                    "dataType": "NUMBER(8,2)",
                                    "name": "ORDER_TOTAL"
                                },
                                {
                                    "comment": "References hr.employees.employee_id.",
                                    "dataType": "NUMBER(6)",
                                    "name": "SALES_REP_ID"
                                },
                                {
                                    "comment": "Sales promotion ID. Used in SH schema",
                                    "dataType": "NUMBER(6)",
                                    "name": "PROMOTION_ID"
                                }
                            ],
                            "databaseName": "",
                            "name": "ORDERS",
                            "schemaName": "\"OE\"",
                            "type": "table"
                        },
                        {
                            "columns": [
                                {
                                    "comment": "Part of concatenated primary key, references orders.order_id.",
                                    "dataType": "NUMBER(12)",
                                    "name": "ORDER_ID"
                                },
                                {
                                    "comment": "Part of concatenated primary key.",
                                    "dataType": "NUMBER(3)",
                                    "name": "LINE_ITEM_ID"
                                },
                                {
                                    "comment": "References product_information.product_id.",
                                    "dataType": "NUMBER(6)",
                                    "name": "PRODUCT_ID"
                                },
                                {
                                    "comment": "",
                                    "dataType": "NUMBER(8,2)",
                                    "name": "UNIT_PRICE"
                                },
                                {
                                    "comment": "",
                                    "dataType": "NUMBER(8)",
                                    "name": "QUANTITY"
                                }
                            ],
                            "databaseName": "",
                            "name": "ORDER_ITEMS",
                            "schemaName": "\"OE\"",
                            "type": "table"
                        },
                        {
                            "columns": [
                                {
                                    "comment": "Primary key column.",
                                    "dataType": "NUMBER(6)",
                                    "name": "PRODUCT_ID"
                                },
                                {
                                    "comment": "Primary key column.",
                                    "dataType": "VARCHAR2(3 byte)",
                                    "name": "LANGUAGE_ID"
                                },
                                {
                                    "comment": "",
                                    "dataType": "NVARCHAR2(50 char)",
                                    "name": "TRANSLATED_NAME"
                                },
                                {
                                    "comment": "",
                                    "dataType": "NVARCHAR2(2000 char)",
                                    "name": "TRANSLATED_DESCRIPTION"
                                }
                            ],
                            "databaseName": "",
                            "name": "PRODUCT_DESCRIPTIONS",
                            "schemaName": "\"OE\"",
                            "type": "table"
                        },
                        {
                            "columns": [
                                {
                                    "comment": "Primary key column.",
                                    "dataType": "NUMBER(6)",
                                    "name": "PRODUCT_ID"
                                },
                                {
                                    "comment": "",
                                    "dataType": "VARCHAR2(50 byte)",
                                    "name": "PRODUCT_NAME"
                                },
                                {
                                    "comment": "Primary language description corresponding to translated_description in\noe.product_descriptions, added to provide non-NLS text columns for OC views\nto accss.",
                                    "dataType": "VARCHAR2(2000 byte)",
                                    "name": "PRODUCT_DESCRIPTION"
                                },
                                {
                                    "comment": "Low cardinality column, can be used for bitmap index.\nSchema SH uses it as foreign key",
                                    "dataType": "NUMBER(2)",
                                    "name": "CATEGORY_ID"
                                },
                                {
                                    "comment": "Low cardinality column, can be used for bitmap index.",
                                    "dataType": "NUMBER(1)",
                                    "name": "WEIGHT_CLASS"
                                },
                                {
                                    "comment": "INTERVAL YEAER TO MONTH column, low cardinality, can be used for bitmap\nindex.",
                                    "dataType": "INTERVAL YEAR(2) TO MONTH(2)",
                                    "name": "WARRANTY_PERIOD"
                                },
                                {
                                    "comment": "Offers possibility of extensions outside Common Schema.",
                                    "dataType": "NUMBER(6)",
                                    "name": "SUPPLIER_ID"
                                },
                                {
                                    "comment": "Check constraint. Appropriate for complex rules, such as \"All products in\nstatus PRODUCTION must have at least one inventory entry.\" Also appropriate\nfor a trigger auditing status change.",
                                    "dataType": "VARCHAR2(20 byte)",
                                    "name": "PRODUCT_STATUS"
                                },
                                {
                                    "comment": "",
                                    "dataType": "NUMBER(8,2)",
                                    "name": "LIST_PRICE"
                                },
                                {
                                    "comment": "",
                                    "dataType": "NUMBER(8,2)",
                                    "name": "MIN_PRICE"
                                },
                                {
                                    "comment": "",
                                    "dataType": "VARCHAR2(50 byte)",
                                    "name": "CATALOG_URL"
                                }
                            ],
                            "databaseName": "",
                            "name": "PRODUCT_INFORMATION",
                            "schemaName": "\"OE\"",
                            "type": "table"
                        },
                        {
                            "columns": [
                                {
                                    "comment": "",
                                    "dataType": "NUMBER(6)",
                                    "name": "PROMO_ID"
                                },
                                {
                                    "comment": "",
                                    "dataType": "VARCHAR2(20 byte)",
                                    "name": "PROMO_NAME"
                                }
                            ],
                            "databaseName": "",
                            "name": "PROMOTIONS",
                            "schemaName": "\"OE\"",
                            "type": "table"
                        }
                    ],
                    "triggers": [
                        {
                            "database": "",
                            "name": "INSERT_ORD_LINE",
                            "schema": "\"OE\""
                        },
                        {
                            "database": "",
                            "name": "ORDERS_ITEMS_TRG",
                            "schema": "\"OE\""
                        },
                        {
                            "database": "",
                            "name": "ORDERS_TRG",
                            "schema": "\"OE\""
                        }
                    ],
                    "views": [
                        {
                            "columns": [
                                {
                                    "comment": "",
                                    "dataType": "UNDEFINED",
                                    "name": "\"ACCT_MGR\""
                                },
                                {
                                    "comment": "",
                                    "dataType": "UNDEFINED",
                                    "name": "\"REGION\""
                                },
                                {
                                    "comment": "",
                                    "dataType": "UNDEFINED",
                                    "name": "\"COUNTRY\""
                                },
                                {
                                    "comment": "",
                                    "dataType": "UNDEFINED",
                                    "name": "\"PROVINCE\""
                                },
                                {
                                    "comment": "",
                                    "dataType": "UNDEFINED",
                                    "name": "\"NUM_CUSTOMERS\""
                                }
                            ],
                            "databaseName": "",
                            "name": "\"ACCOUNT_MANAGERS\"",
                            "schemaName": "\"OE\"",
                            "type": "view"
                        }
                    ]
                }
            ],
            "supportsCatalogs": true,
            "supportsSchemas": true
        }
    ]
}
```

## Sample Indication

The above sample has the same structure as

```json
{
    "createTime":"", //export time
    "createdBy":"sqlflow-exporter",//name of the export tool
    "physicalInstance":"",//server address
    "servers":[
        {
            "name":"",//server name
            "dbVendor":"",//database type，possible values are: dbvathena,dbvazuresql,dbvbigquery,dbvcouchbase,dbvdb2,dbvgreenplum,dbvhana,dbvhive,dbvimpala,dbvinformix,dbvmdx,dbvmysqldbvnetezza,dbvopenedge,dbvoracle,dbvpostgresql,dbvpresto,dbvredshift,dbvsnowflake,dbvsparksql,dbvmssql,dbvsybase,dbvteradata,dbvvertica
            "supportsCatalogs":true,// has database layer
            "supportsSchemas":true,// has schema layer
            "databases":[ // No extra db unit field outside the database list because all units belong to the specific schema and database.
                {
                    "name":"",//database name
                    "schemas":[
                        {
                            "name":"",//schema name
                            "synonyms":[
                                {
                                    "name":"",
                                    "sourceName":"",
                                    "sourceSchema":"",
                                    "sourceDbLinkName":""
                                }
                            ],
                            "sequences":[
                                {
                                    "name":"",
                                    "incrementBy":""
                                }
                            ],
                            "tables":[
                                {
                                    "name":"",//table name 
                                    "columns":[
                                        {
                                            "dataType":"",//column data type
                                            "name":"",//column name
                                            "comment":""//column comment
                                        }
                                    ]
                                }
                            ],
                            "views":[ 
                              {
                                    "name":"",//view name
                                    "columns":[
                                        {
                                            "dataType":"",
                                            "name":"",
                                            "comment":""
                                        }
                                    ]
                                }
                            ],
                            "others":[//others, including resultset, variable, path etc 
                                {
                                    "name":"",
                                    "columns":[
                                        {
                                            "dataType":"",
                                            "name":"",
                                            "comment":""
                                        }
                                    ]
                                }
                            ],
                            "packages":[
                                {
                                    "name":"",//package name 
                                    "procedures":[//prcedures in the package
                                    ],
                                    "functions":[//functions in the package
                                    ],
                                    "triggers":[//triggers in the package
                                    ]
                                }
                            ],
                            "procedures":[
                                {
                                    "name":"",
                                    "type":"",
                                    "arguments":[
                                        {
                                            "name":"",
                                            "dataType":"",
                                            "inout":""
                                        }
                                    ]
                                }
                            ],
                            "functions":[
                                {
                                    "name":"",
                                    "type":"",
                                    "arguments":[
                                        {
                                            "name":"",
                                            "dataType":"",
                                            "inout":""
                                        }
                                    ]
                                }
                            ],
                            "triggers":[
                                {
                                    "name":"",
                                    "type":"",
                                    "arguments":[
                                        {
                                            "name":"",
                                            "dataType":"",
                                            "inout":""
                                        }
                                    ]
                                }
                            ]
                        }
                    ],
            "dbLinks":[
                {
                    "owner":"",
                    "name":"",
                    "userName":"",
                    "host":""
                }
            ],
            "queries":[//DDL scripts in database
                {
                    "database":"",
                    "schema":"",
                    "name":"",
                    "type":"",
                    "sourceCode":"",
                    "groupName":""
                }
            ]
        }
    ],
    "errorMessages":[//errors during the exporting 
        {
            "errorMessage":"",
            "errorType":"",
            "file":""
        }
    ]
  }
```

## Get More Details

You can refer to [this section](../../introduction/java-library/usage/dataflow.xml-structure.md) to understand more about what does each field mean.
