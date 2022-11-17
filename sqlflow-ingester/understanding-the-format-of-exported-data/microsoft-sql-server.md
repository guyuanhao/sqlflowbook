---
description: >-
  metadata.json exported by ingester has the same structure as the
  dbobjs.servers part of the Dlineage tool result
---

# Microsoft SQL Server

This page gives a sample metadata for **Microsoft SQL Server**.

## Sample

```json
{
    "createTime": "2022-11-16 21:05:32",
    "createdBy": "sqlflow-ingester v1.1.7",
    "physicalInstance": "115.159.xx.xx",
    "servers": [
        {
            "databases": [
                {
                    "name": "HR",
                    "schemas": [
                        {
                            "name": "[dbo]",
                            "synonyms": [
                                {
                                    "database": "[HR]",
                                    "name": "OFFICES",
                                    "schema": "[dbo]",
                                    "sourceDbLinkName": "HR",
                                    "sourceName": "LOCATIONS",
                                    "sourceSchema": "DBO"
                                }
                            ],
                            "tables": [
                                {
                                    "columns": [
                                        {
                                            "comment": "",
                                            "dataType": "char(2)",
                                            "name": "COUNTRY_ID"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "varchar(40)",
                                            "name": "COUNTRY_NAME"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "int",
                                            "name": "REGION_ID"
                                        }
                                    ],
                                    "databaseName": "[HR]",
                                    "name": "COUNTRIES",
                                    "schemaName": "[dbo]",
                                    "type": "table"
                                },
                                {
                                    "columns": [
                                        {
                                            "comment": "",
                                            "dataType": "int",
                                            "name": "DEPARTMENT_ID"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "varchar(30)",
                                            "name": "DEPARTMENT_NAME"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "int",
                                            "name": "MANAGER_ID"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "int",
                                            "name": "LOCATION_ID"
                                        }
                                    ],
                                    "databaseName": "[HR]",
                                    "name": "DEPARTMENTS",
                                    "schemaName": "[dbo]",
                                    "type": "table"
                                },
                                {
                                    "columns": [
                                        {
                                            "comment": "",
                                            "dataType": "int",
                                            "name": "EMPLOYEE_ID"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "varchar(20)",
                                            "name": "FIRST_NAME"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "varchar(25)",
                                            "name": "LAST_NAME"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "varchar(25)",
                                            "name": "EMAIL"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "varchar(20)",
                                            "name": "PHONE_INT"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "date",
                                            "name": "HIRE_DATE"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "varchar(10)",
                                            "name": "JOB_ID"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "int",
                                            "name": "SALARY"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "int",
                                            "name": "COMMISSION_PCT"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "int",
                                            "name": "MANAGER_ID"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "int",
                                            "name": "DEPARTMENT_ID"
                                        }
                                    ],
                                    "databaseName": "[HR]",
                                    "name": "EMPLOYEES",
                                    "schemaName": "[dbo]",
                                    "type": "table"
                                },
                                {
                                    "columns": [
                                        {
                                            "comment": "",
                                            "dataType": "int",
                                            "name": "EMPLOYEE_ID"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "date",
                                            "name": "START_DATE"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "date",
                                            "name": "END_DATE"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "varchar(10)",
                                            "name": "JOB_ID"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "int",
                                            "name": "DEPARTMENT_ID"
                                        }
                                    ],
                                    "databaseName": "[HR]",
                                    "name": "JOB_HISTORY",
                                    "schemaName": "[dbo]",
                                    "type": "table"
                                },
                                {
                                    "columns": [
                                        {
                                            "comment": "",
                                            "dataType": "varchar(10)",
                                            "name": "JOB_ID"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "varchar(35)",
                                            "name": "JOB_TITLE"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "int",
                                            "name": "MIN_SALARY"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "int",
                                            "name": "MAX_SALARY"
                                        }
                                    ],
                                    "databaseName": "[HR]",
                                    "name": "JOBS",
                                    "schemaName": "[dbo]",
                                    "type": "table"
                                },
                                {
                                    "columns": [
                                        {
                                            "comment": "",
                                            "dataType": "int",
                                            "name": "LOCATION_ID"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "varchar(40)",
                                            "name": "STREET_ADDRESS"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "varchar(12)",
                                            "name": "POSTAL_CODE"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "varchar(30)",
                                            "name": "CITY"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "varchar(25)",
                                            "name": "STATE_PROVINCE"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "char(2)",
                                            "name": "COUNTRY_ID"
                                        }
                                    ],
                                    "databaseName": "[HR]",
                                    "name": "LOCATIONS",
                                    "schemaName": "[dbo]",
                                    "type": "table"
                                },
                                {
                                    "columns": [
                                        {
                                            "comment": "",
                                            "dataType": "int",
                                            "name": "REGION_ID"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "varchar(25)",
                                            "name": "REGION_NAME"
                                        }
                                    ],
                                    "databaseName": "[HR]",
                                    "name": "REGIONS",
                                    "schemaName": "[dbo]",
                                    "type": "table"
                                }
                            ],
                            "views": [
                                {
                                    "columns": [
                                        {
                                            "comment": "",
                                            "dataType": "int",
                                            "name": "[employee_id]"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "varchar(10)",
                                            "name": "[job_id]"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "int",
                                            "name": "[manager_id]"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "int",
                                            "name": "[department_id]"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "int",
                                            "name": "[location_id]"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "char(2)",
                                            "name": "[country_id]"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "varchar(20)",
                                            "name": "[first_name]"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "varchar(25)",
                                            "name": "[last_name]"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "int",
                                            "name": "[salary]"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "int",
                                            "name": "[commission_pct]"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "varchar(30)",
                                            "name": "[department_name]"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "varchar(35)",
                                            "name": "[job_title]"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "varchar(30)",
                                            "name": "[city]"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "varchar(25)",
                                            "name": "[state_province]"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "varchar(40)",
                                            "name": "[country_name]"
                                        },
                                        {
                                            "comment": "",
                                            "dataType": "varchar(25)",
                                            "name": "[region_name]"
                                        }
                                    ],
                                    "databaseName": "[HR]",
                                    "name": "[EMP_DETAILS_VIEW]",
                                    "schemaName": "[dbo]",
                                    "type": "view"
                                }
                            ]
                        }
                    ]
                }
            ],
            "dbLinks": [],
            "dbVendor": "dbvmssql",
            "name": "115.159.xx.xx",
            "queries": [
                {
                    "database": "DWDB",
                    "groupName": "",
                    "name": "SPREPORTER_COMPARE_OVERVIEW_BATCHUNIQUEHASHINFO",
                    "schema": "READTRACE",
                    "sourceCode": "\r\ncreate procedure ReadTrace.spReporter_Compare_Overview_BatchUniqueHashInfo\r\nas\r\nbegin\r\n\tset nocount on\r\n\r\n\tselect 'Matching' as [Desc],\r\n\t\t\tcount_big(*) as [Count]\r\n\t\t\tfrom ReadTrace.tblUniqueBatches b\r\n\t\t\tinner join ReadTraceCompare.tblUniqueBatches c\r\n\t\t\t\ton b.HashID = c.HashID\r\n\t\r\n\tunion all\r\n\t\tselect 'BO' as [Desc],\r\n\t\t\t\tcount_big(*) \r\n\t\t\t\tfrom ReadTrace.tblUniqueBatches b\r\n\t\t\t\tleft outer join ReadTraceCompare.tblUniqueBatches c\r\n\t\t\t\t\ton b.HashID = c.HashID\r\n\t\t\t\twhere c.HashID is NULL\r\n\r\n\tunion all\r\n\t\tselect 'CO' as [Desc],\r\n\t\t\t\tcount_big(*) \r\n\t\t\t\tfrom ReadTrace.tblUniqueBatches b\r\n\t\t\t\tright outer join ReadTraceCompare.tblUniqueBatches c\r\n\t\t\t\t\ton b.HashID = c.HashID\r\n\t\t\t\twhere b.HashID is NULL\r\n\torder by [Desc]\r\nend ",
                    "type": "procedure"
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
