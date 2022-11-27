---
description: >-
  metadata.json exported by ingester has the same structure as the
  dbobjs.servers part of the Dlineage tool result
---

# Oracle

This page gives a sample metadata for **Oracle**.

## Sample

```json
{
    "createTime": "2022-11-17 00:54:06",
    "createdBy": "sqlflow-ingester v1.1.8",
    "physicalInstance": "106.54.xx.xx",
    "servers": [
        {
            "databases": [
                {
                    "name": "ORCL",
                    "schemas": [
                        {
                            "name": "\"BIGKING\"",
                            "packages": [
                                {
                                    "databaseName": "\"ORCL\"",
                                    "functions": [
                                        {
                                            "arguments": [
                                                {
                                                    "dataType": "VARCHAR2",
                                                    "name": "IN_STATUS"
                                                }
                                            ],
                                            "databaseName": "\"ORCL\"",
                                            "name": "F_C_GETSTAFFNUM",
                                            "schemaName": "\"BIGKING\""
                                        }
                                    ],
                                    "name": "CHEN_PACK",
                                    "procedures": [
                                        {
                                            "arguments": [
                                                {
                                                    "dataType": "VARCHAR2",
                                                    "name": "RECEIVER"
                                                },
                                                {
                                                    "dataType": "VARCHAR2",
                                                    "name": "CONTENT"
                                                }
                                            ],
                                            "databaseName": "\"ORCL\"",
                                            "name": "P_C_SENDMSG",
                                            "schemaName": "\"BIGKING\""
                                        }
                                    ],
                                    "schemaName": "\"BIGKING\""
                                },
                                {
                                    "databaseName": "\"ORCL\"",
                                    "name": "TESTSQLFLOW",
                                    "procedures": [
                                        {
                                            "databaseName": "\"ORCL\"",
                                            "name": "MYSQLFLOW",
                                            "schemaName": "\"BIGKING\""
                                        }
                                    ],
                                    "schemaName": "\"BIGKING\""
                                }
                            ],
                            "procedures": [
                                {
                                    "arguments": [
                                        {
                                            "dataType": "NUMBER",
                                            "name": "EVALUATION_ID"
                                        },
                                        {
                                            "dataType": "NUMBER",
                                            "name": "EMPLOYEE_ID"
                                        },
                                        {
                                            "dataType": "DATE",
                                            "name": "EVALUATION_DATE"
                                        }
                                    ],
                                    "databaseName": "\"ORCL\"",
                                    "name": "ADD_EVALUATION",
                                    "schemaName": "\"BIGKING\""
                                },
                                {
                                    "databaseName": "\"ORCL\"",
                                    "name": "EMP_COUNT",
                                    "schemaName": "\"BIGKING\""
                                }
                            ],
                            "tables": [
                                {
                                    "columns": [
                                        {
                                            "comment": "",
                                            "dataType": "VARCHAR2(100 byte)",
                                            "name": "A"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "CHAR(1 byte)",
                                            "name": "COLUMN1"
                                        }
                                    ],
                                    "databaseName": "\"ORCL\"",
                                    "name": "AA",
                                    "schemaName": "\"BIGKING\"",
                                    "type": "table"
                                },
                                {
                                    "columns": [
                                        {
                                            "comment": "",
                                            "dataType": "CHAR(1 byte)",
                                            "name": "COLUMN1"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "CHAR(1 byte)",
                                            "name": "columN1"
                                        }
                                    ],
                                    "databaseName": "\"ORCL\"",
                                    "name": "Test13",
                                    "schemaName": "\"BIGKING\"",
                                    "type": "table"
                                }
                            ],
                            "triggers": [
                                {
                                    "databaseName": "\"ORCL\"",
                                    "name": "AA_TR",
                                    "schemaName": "\"BIGKING\""
                                }
                            ],
                            "views": [
                                {
                                    "columns": [
                                        {
                                            "comment": "",
                                            "dataType": "NUMBER(38,0)",
                                            "name": "\"ID\""
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "VARCHAR2(36 byte)",
                                            "name": "\"NAME\""
                                        }
                                    ],
                                    "databaseName": "\"ORCL\"",
                                    "name": "\"V_TEST\"",
                                    "schemaName": "\"BIGKING\"",
                                    "type": "view"
                                },
                                {
                                    "columns": [
                                        {
                                            "comment": "",
                                            "dataType": "NUMBER(38,0)",
                                            "name": "\"ID\""
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "VARCHAR2(36 byte)",
                                            "name": "\"NAME\""
                                        }
                                    ],
                                    "databaseName": "\"ORCL\"",
                                    "name": "\"V_TEST1\"",
                                    "schemaName": "\"BIGKING\"",
                                    "type": "view"
                                }
                            ]
                        }
                    ]
                }
            ],
            "dbLinks": [
                {
                    "host": "orcl",
                    "name": "\"LINK_TEST\"",
                    "owner": "\"PUBLIC\"",
                    "userName": "\"BIGKING\""
                },
                {
                    "host": "orcl",
                    "name": "\"LINK_TEST5.LOCALDOMAIN\"",
                    "owner": "\"PUBLIC\"",
                    "userName": "\"BIGKING\""
                },
                {
                    "host": "orcl",
                    "name": "\"LINK_TEST4.LOCALDOMAIN\"",
                    "owner": "\"PUBLIC\"",
                    "userName": "\"BIGKING\""
                },
                {
                    "host": "orcl",
                    "name": "\"LINK_TEST3\"",
                    "owner": "\"PUBLIC\"",
                    "userName": "\"BIGKING\""
                }
            ],
            "dbVendor": "dbvoracle",
            "name": "106.54.xx.xx",
            "queries": [
                {
                    "database": "ORCL",
                    "groupName": "\"SH\".\"FWEEK_PSCAT_SALES_MV\"",
                    "name": "FWEEK_PSCAT_SALES_MV",
                    "schema": "SH",
                    "sourceCode": "CREATE MATERIALIZED VIEW \"SH\".\"FWEEK_PSCAT_SALES_MV\" as SELECT   t.week_ending_day\n  ,        p.prod_subcategory\n  ,        sum(s.amount_sold) AS dollars\n  ,        s.channel_id\n  ,        s.promo_id\n  FROM     sales s\n  ,        times t\n  ,        products p\n  WHERE    s.time_id = t.time_id\n  AND      s.prod_id = p.prod_id\n  GROUP BY t.week_ending_day\n  ,        p.prod_subcategory\n  ,        s.channel_id\n  ,        s.promo_id",
                    "type": "materialized view"
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
