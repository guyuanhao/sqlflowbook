# Microsoft SQL Server

This page gives a sample metadata for **Microsoft SQL Server**.

```json
{
    "servers": [
        {
            "name": "DEFAULT_SERVER",
            "dbVendor": "dbvmssql",
            "supportsCatalogs": true,
            "supportsSchemas": true,
            "databases": [
                {
                    "name": "DEFAULT",
                    "schemas": [
                        {
                            "name": "DEFAULT",
                            "views": [
                                {
                                    "id": "35",
                                    "name": "vsal",
                                    "displayName": "vsal",
                                    "type": "view",
                                    "columns": [
                                        {
                                            "id": "37",
                                            "name": "\"Department\"",
                                            "coordinates": [
                                                {
                                                    "hashCode": "0",
                                                    "x": 3,
                                                    "y": 36
                                                },
                                                {
                                                    "hashCode": "0",
                                                    "x": 3,
                                                    "y": 48
                                                }
                                            ]
                                        },
                                        {
                                            "id": "38",
                                            "name": "\"Employees\"",
                                            "coordinates": [
                                                {
                                                    "hashCode": "0",
                                                    "x": 4,
                                                    "y": 36
                                                },
                                                {
                                                    "hashCode": "0",
                                                    "x": 4,
                                                    "y": 47
                                                }
                                            ]
                                        },
                                        {
                                            "id": "39",
                                            "name": "\"Salary\"",
                                            "coordinates": [
                                                {
                                                    "hashCode": "0",
                                                    "x": 5,
                                                    "y": 36
                                                },
                                                {
                                                    "hashCode": "0",
                                                    "x": 5,
                                                    "y": 44
                                                }
                                            ]
                                        },
                                        {
                                            "id": "34",
                                            "name": "RelationRows",
                                            "coordinates": [
                                                {
                                                    "hashCode": "0",
                                                    "x": 1,
                                                    "y": 13
                                                },
                                                {
                                                    "hashCode": "0",
                                                    "x": 1,
                                                    "y": 17
                                                }
                                            ],
                                            "source": "system",
                                            "uiVisible": false
                                        }
                                    ],
                                    "coordinates": [
                                        {
                                            "hashCode": "0",
                                            "x": 1,
                                            "y": 13
                                        },
                                        {
                                            "hashCode": "0",
                                            "x": 1,
                                            "y": 17
                                        }
                                    ]
                                }
                            ],
                            "others": [
                                {
                                    "id": "2",
                                    "name": "RESULT_OF_A-1",
                                    "displayName": "RESULT_OF_A-1",
                                    "type": "select_list",
                                    "columns": [
                                        {
                                            "id": "1",
                                            "name": "RelationRows",
                                            "coordinates": [
                                                {
                                                    "hashCode": "0",
                                                    "x": 11,
                                                    "y": 29
                                                },
                                                {
                                                    "hashCode": "0",
                                                    "x": 11,
                                                    "y": 30
                                                }
                                            ],
                                            "source": "system",
                                            "uiVisible": false
                                        },
                                        {
                                            "id": "10",
                                            "name": "deptno",
                                            "coordinates": [
                                                {
                                                    "hashCode": "0",
                                                    "x": 6,
                                                    "y": 18
                                                },
                                                {
                                                    "hashCode": "0",
                                                    "x": 6,
                                                    "y": 24
                                                }
                                            ]
                                        },
                                        {
                                            "id": "11",
                                            "name": "num_emp",
                                            "coordinates": [
                                                {
                                                    "hashCode": "0",
                                                    "x": 7,
                                                    "y": 18
                                                },
                                                {
                                                    "hashCode": "0",
                                                    "x": 7,
                                                    "y": 34
                                                }
                                            ]
                                        },
                                        {
                                            "id": "15",
                                            "name": "sal_sum",
                                            "coordinates": [
                                                {
                                                    "hashCode": "0",
                                                    "x": 8,
                                                    "y": 18
                                                },
                                                {
                                                    "hashCode": "0",
                                                    "x": 8,
                                                    "y": 34
                                                }
                                            ]
                                        }
                                    ],
                                    "coordinates": [
                                        {
                                            "hashCode": "0",
                                            "x": 11,
                                            "y": 29
                                        },
                                        {
                                            "hashCode": "0",
                                            "x": 11,
                                            "y": 30
                                        }
                                    ]
                                },
                                {
                                    "id": "20",
                                    "name": "RESULT_OF_B-1",
                                    "displayName": "RESULT_OF_B-1",
                                    "type": "select_list",
                                    "columns": [
                                        {
                                            "id": "19",
                                            "name": "RelationRows",
                                            "coordinates": [
                                                {
                                                    "hashCode": "0",
                                                    "x": 15,
                                                    "y": 32
                                                },
                                                {
                                                    "hashCode": "0",
                                                    "x": 15,
                                                    "y": 33
                                                }
                                            ],
                                            "source": "system",
                                            "uiVisible": false
                                        },
                                        {
                                            "id": "21",
                                            "name": "total_count",
                                            "coordinates": [
                                                {
                                                    "hashCode": "0",
                                                    "x": 12,
                                                    "y": 18
                                                },
                                                {
                                                    "hashCode": "0",
                                                    "x": 12,
                                                    "y": 38
                                                }
                                            ]
                                        },
                                        {
                                            "id": "25",
                                            "name": "total_sal",
                                            "coordinates": [
                                                {
                                                    "hashCode": "0",
                                                    "x": 13,
                                                    "y": 18
                                                },
                                                {
                                                    "hashCode": "0",
                                                    "x": 13,
                                                    "y": 36
                                                }
                                            ]
                                        }
                                    ],
                                    "coordinates": [
                                        {
                                            "hashCode": "0",
                                            "x": 15,
                                            "y": 32
                                        },
                                        {
                                            "hashCode": "0",
                                            "x": 15,
                                            "y": 33
                                        }
                                    ]
                                },
                                {
                                    "id": "30",
                                    "name": "RS-1",
                                    "displayName": "RS-1",
                                    "type": "select_list",
                                    "columns": [
                                        {
                                            "id": "31",
                                            "name": "\"Department\"",
                                            "coordinates": [
                                                {
                                                    "hashCode": "0",
                                                    "x": 3,
                                                    "y": 10
                                                },
                                                {
                                                    "hashCode": "0",
                                                    "x": 3,
                                                    "y": 48
                                                }
                                            ]
                                        },
                                        {
                                            "id": "32",
                                            "name": "\"Employees\"",
                                            "coordinates": [
                                                {
                                                    "hashCode": "0",
                                                    "x": 4,
                                                    "y": 10
                                                },
                                                {
                                                    "hashCode": "0",
                                                    "x": 4,
                                                    "y": 47
                                                }
                                            ]
                                        },
                                        {
                                            "id": "33",
                                            "name": "\"Salary\"",
                                            "coordinates": [
                                                {
                                                    "hashCode": "0",
                                                    "x": 5,
                                                    "y": 10
                                                },
                                                {
                                                    "hashCode": "0",
                                                    "x": 5,
                                                    "y": 44
                                                }
                                            ]
                                        },
                                        {
                                            "id": "29",
                                            "name": "RelationRows",
                                            "coordinates": [
                                                {
                                                    "hashCode": "0",
                                                    "x": 3,
                                                    "y": 10
                                                },
                                                {
                                                    "hashCode": "0",
                                                    "x": 5,
                                                    "y": 44
                                                }
                                            ],
                                            "source": "system",
                                            "uiVisible": false
                                        }
                                    ],
                                    "coordinates": [
                                        {
                                            "hashCode": "0",
                                            "x": 3,
                                            "y": 10
                                        },
                                        {
                                            "hashCode": "0",
                                            "x": 5,
                                            "y": 44
                                        }
                                    ]
                                }
                            ],
                            "processes": [
                                {
                                    "id": "36",
                                    "name": "Query Create View-1",
                                    "procedureName": "batchQueries",
                                    "queryHashId": "4ef278b9a7850f717990e96aae7a3f43",
                                    "coordinates": [
                                        {
                                            "hashCode": "0",
                                            "x": 1,
                                            "y": 1
                                        },
                                        {
                                            "hashCode": "0",
                                            "x": 16,
                                            "y": 2
                                        }
                                    ],
                                    "uiVisible": false
                                }
                            ]
                        },
                        {
                            "name": "scott",
                            "tables": [
                                {
                                    "id": "6",
                                    "name": "emp",
                                    "displayName": "scott.emp",
                                    "type": "table",
                                    "columns": [
                                        {
                                            "id": "5",
                                            "name": "RelationRows",
                                            "coordinates": [
                                                {
                                                    "hashCode": "0",
                                                    "x": 9,
                                                    "y": 18
                                                },
                                                {
                                                    "hashCode": "0",
                                                    "x": 9,
                                                    "y": 27
                                                }
                                            ],
                                            "source": "system",
                                            "uiVisible": false
                                        },
                                        {
                                            "id": "9",
                                            "name": "city",
                                            "coordinates": [
                                                {
                                                    "hashCode": "0",
                                                    "x": 10,
                                                    "y": 18
                                                },
                                                {
                                                    "hashCode": "0",
                                                    "x": 10,
                                                    "y": 22
                                                }
                                            ]
                                        },
                                        {
                                            "id": "7",
                                            "name": "deptno",
                                            "coordinates": [
                                                {
                                                    "hashCode": "0",
                                                    "x": 6,
                                                    "y": 18
                                                },
                                                {
                                                    "hashCode": "0",
                                                    "x": 6,
                                                    "y": 24
                                                }
                                            ]
                                        },
                                        {
                                            "id": "8",
                                            "name": "sal",
                                            "coordinates": [
                                                {
                                                    "hashCode": "0",
                                                    "x": 8,
                                                    "y": 22
                                                },
                                                {
                                                    "hashCode": "0",
                                                    "x": 8,
                                                    "y": 25
                                                }
                                            ]
                                        }
                                    ],
                                    "coordinates": [
                                        {
                                            "hashCode": "0",
                                            "x": 9,
                                            "y": 18
                                        },
                                        {
                                            "hashCode": "0",
                                            "x": 9,
                                            "y": 27
                                        }
                                    ]
                                }
                            ]
                        }
                    ]
                }
            ]
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
