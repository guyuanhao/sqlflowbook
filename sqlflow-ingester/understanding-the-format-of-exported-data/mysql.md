# MySQL

This page gives a sample metadata for **MySQL**.

## Sample

```json
{
    "createTime": "2022-11-16 21:01:50",
    "createdBy": "sqlflow-ingester v1.1.7",
    "physicalInstance": "115.159.xx.xx",
    "servers": [
        {
            "databases": [
                {
                    "name": "SQLFlowDB1",
                    "tables": [
                        {
                            "columns": [
                                {
                                    "comment": "",
                                    "dataType": "int",
                                    "name": "ID"
                                }
                            ],
                            "databaseName": "`SQLFlowDB1`",
                            "name": "ABC",
                            "schemaName": "",
                            "type": "table"
                        },
                        {
                            "columns": [
                                {
                                    "comment": "",
                                    "dataType": "int",
                                    "name": "ID"
                                }
                            ],
                            "databaseName": "`SQLFlowDB1`",
                            "name": "BCD",
                            "schemaName": "",
                            "type": "table"
                        },
                        {
                            "columns": [
                                {
                                    "comment": "",
                                    "dataType": "int",
                                    "name": "ID"
                                },
                                {
                                    "comment": "",
                                    "dataType": "varchar",
                                    "name": "NAME"
                                },
                                {
                                    "comment": "",
                                    "dataType": "varchar",
                                    "name": "COMMITSTR"
                                }
                            ],
                            "databaseName": "`SQLFlowDB1`",
                            "name": "TABLEA",
                            "schemaName": "",
                            "type": "table"
                        },
                        {
                            "columns": [
                                {
                                    "comment": "",
                                    "dataType": "int",
                                    "name": "ID"
                                },
                                {
                                    "comment": "",
                                    "dataType": "varchar",
                                    "name": "NAME"
                                },
                                {
                                    "comment": "",
                                    "dataType": "varchar",
                                    "name": "COMMITSTR"
                                }
                            ],
                            "databaseName": "`SQLFlowDB1`",
                            "name": "TABLEB",
                            "schemaName": "",
                            "type": "table"
                        }
                    ]
                }
            ],
            "dbLinks": [],
            "dbVendor": "dbvmysql",
            "name": "115.159.xx.xx",
            "queries": [
                {
                    "database": "employees",
                    "groupName": "",
                    "name": "DEPT_EMP_LATEST_DATE",
                    "sourceCode": "CREATE ALGORITHM=UNDEFINED DEFINER=`root`@`58.56.46.106` SQL SECURITY DEFINER VIEW `dept_emp_latest_date` AS select `dept_emp`.`emp_no` AS `emp_no`,max(`dept_emp`.`from_date`) AS `from_date`,max(`dept_emp`.`to_date`) AS `to_date` from `dept_emp` group by `dept_emp`.`emp_no`",
                    "type": "view"
                }
            ],
            "supportsCatalogs": true,
            "supportsSchemas": false
        }
    ]
}
```

## Sample Indication

```json
{
    "createTime":"", //export time
    "createdBy":"sqlflow-exporter",//name of the export tool
    "physicalInstance":"",//server address
    "servers":[
        {
            "name":"",//server name
            "dbVendor":"",//database type，possible values are: dbvathena,dbvazuresql,dbvbigquery,dbvcouchbase,dbvdb2,dbvgreenplum,dbvhana,dbvhive,dbvimpala,dbvinformix,dbvmdx,dbvmysqldbvnetezza,dbvopenedge,dbvoracle,dbvpostgresql,dbvpresto,dbvredshift,dbvsnowflake,dbvsparksql,dbvmssql,dbvsybase,dbvteradata,dbvvertica
            "supportsCatalogs":true,//there's a database layer
            "supportsSchemas":false,//there's no schema layer
            "databases":[
                {
                    "name":"",//database name
    
                    "synonyms":[//synonym list when there's no schema object, same structure as the above servers.databases.schemas.synonyms
  
                    ],
                    "sequences":[//sequence list when there's no schema object, same structure as the above servers.databases.schemas.sequences 
  
                    ],
                    "tables":[//table list when there's no schema object, same structure as the above servers.databases.schemas.tables 
  
  
                    ],
                    "views":[//view list when there's no schema object, same structure as the above servers.databases.schemas.views 
  
                    ],
                    "others":[//others when there's no schema object, including resultset, variable, path etc. same structure as the above servers.databases.schemas.others 
  
                    ],
                    "packages":[//package list when there's no schema object, same structure as the above servers.databases.schemas.packages 
  
                    ],
                    "procedures":[//procedure list when there's no schema object, same structure as the above servers.databases.schemas.procedures 
  
                    ],
                    "functions":[//function list when there's no schema object, same structure as the above servers.databases.schemas.functions 
  
                    ],
                    "triggers":[//trigger list when there's no schema object, same structure as the above servers.databases.schemas.triggers 
  
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
