---
description: >-
  metadata.json exported by ingester has the same structure as the
  dbobjs.servers part of the Dlineage tool result
---

# PostgreSQL

This page gives a sample metadata for **PostgreSQL**.

## Sample

```json
{
    "createTime": "2022-11-16 05:05:45",
    "createdBy": "sqlflow-ingester v1.1.8",
    "physicalInstance": "115.159.xx.xx",
    "servers": [
        {
            "databases": [
                {
                    "name": "kingland",
                    "schemas": [
                        {
                            "name": "\"dbt_jaffle_shop\"",
                            "tables": [
                                {
                                    "columns": [
                                        {
                                            "comment": "",
                                            "dataType": "integer",
                                            "name": "CUSTOMER_ID"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "text",
                                            "name": "FIRST_NAME"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "text",
                                            "name": "LAST_NAME"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "date",
                                            "name": "FIRST_ORDER"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "date",
                                            "name": "MOST_RECENT_ORDER"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "bigint",
                                            "name": "NUMBER_OF_ORDERS"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "bigint",
                                            "name": "CUSTOMER_LIFETIME_VALUE"
                                        }
                                    ],
                                    "name": "customers",
                                    "type": "table"
                                },
                                {
                                    "columns": [
                                        {
                                            "comment": "",
                                            "dataType": "integer",
                                            "name": "ORDER_ID"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "integer",
                                            "name": "CUSTOMER_ID"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "date",
                                            "name": "ORDER_DATE"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "text",
                                            "name": "STATUS"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "bigint",
                                            "name": "CREDIT_CARD_AMOUNT"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "bigint",
                                            "name": "COUPON_AMOUNT"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "bigint",
                                            "name": "BANK_TRANSFER_AMOUNT"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "bigint",
                                            "name": "GIFT_CARD_AMOUNT"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "bigint",
                                            "name": "AMOUNT"
                                        }
                                    ],
                                    "name": "orders",
                                    "type": "table"
                                },
                                {
                                    "columns": [
                                        {
                                            "comment": "",
                                            "dataType": "integer",
                                            "name": "ID"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "text",
                                            "name": "FIRST_NAME"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "text",
                                            "name": "LAST_NAME"
                                        }
                                    ],
                                    "name": "raw_customers",
                                    "type": "table"
                                },
                                {
                                    "columns": [
                                        {
                                            "comment": "",
                                            "dataType": "integer",
                                            "name": "ID"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "integer",
                                            "name": "USER_ID"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "date",
                                            "name": "ORDER_DATE"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "text",
                                            "name": "STATUS"
                                        }
                                    ],
                                    "name": "raw_orders",
                                    "type": "table"
                                },
                                {
                                    "columns": [
                                        {
                                            "comment": "",
                                            "dataType": "integer",
                                            "name": "ID"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "integer",
                                            "name": "ORDER_ID"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "text",
                                            "name": "PAYMENT_METHOD"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "integer",
                                            "name": "AMOUNT"
                                        }
                                    ],
                                    "name": "raw_payments",
                                    "type": "table"
                                }
                            ],
                            "views": [
                                {
                                    "columns": [
                                        {
                                            "comment": "",
                                            "dataType": "integer",
                                            "name": "\"customer_id\""
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "text",
                                            "name": "\"first_name\""
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "text",
                                            "name": "\"last_name\""
                                        }
                                    ],
                                    "name": "\"stg_customers\"",
                                    "type": "view"
                                },
                                {
                                    "columns": [
                                        {
                                            "comment": "",
                                            "dataType": "integer",
                                            "name": "\"customer_id\""
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "text",
                                            "name": "\"first_name\""
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "text",
                                            "name": "\"last_name\""
                                        }
                                    ],
                                    "name": "\"stg_customers123\"",
                                    "type": "view"
                                },
                                {
                                    "columns": [
                                        {
                                            "comment": "",
                                            "dataType": "integer",
                                            "name": "\"order_id\""
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "integer",
                                            "name": "\"customer_id\""
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "date",
                                            "name": "\"order_date\""
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "text",
                                            "name": "\"status\""
                                        }
                                    ],
                                    "name": "\"stg_orders\"",
                                    "type": "view"
                                },
                                {
                                    "columns": [
                                        {
                                            "comment": "",
                                            "dataType": "integer",
                                            "name": "\"payment_id\""
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "integer",
                                            "name": "\"order_id\""
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "text",
                                            "name": "\"payment_method\""
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "integer",
                                            "name": "\"amount\""
                                        }
                                    ],
                                    "name": "\"stg_payments\"",
                                    "type": "view"
                                }
                            ]
                        }
                    ]
                }
            ],
            "dbLinks": [],
            "dbVendor": "dbvpostgresql",
            "name": "115.159.xx.xx",
            "queries": [
                {
                    "database": "kingland",
                    "groupName": "",
                    "name": "stg_customers",
                    "schema": "dbt_jaffle_shop",
                    "sourceCode": "CREATE VIEW stg_customers AS  WITH source AS (\n         SELECT raw_customers.id,\n            raw_customers.first_name,\n            raw_customers.last_name\n           FROM dbt_jaffle_shop.raw_customers\n        ), renamed AS (\n         SELECT source.id AS customer_id,\n            source.first_name,\n            source.last_name\n           FROM source\n        )\n SELECT renamed.customer_id,\n    renamed.first_name,\n    renamed.last_name\n   FROM renamed;",
                    "type": "view"
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
