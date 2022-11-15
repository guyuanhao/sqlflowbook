---
description: >-
  https://e.gitee.com/gudusoft/projects/151613/docs/617965/file/1485427?sub_id=6032663
---

# Understand the format of exported data

This page gives an example and some clarifications on the format of the SQLFlow-Ingester exported data.

We may have some similar fields in the exported json data due to the fact that different databases can have various structure concepts. These similar fields won't all appear in a real case. &#x20;

Following json is an exhaustive example which lists all possible fields:

```json
{
  "createTime":"", //export time
  "createdBy":"sqlflow-exporter",//name of the export tool
  "physicalInstance":"",//server address
  "servers":[
      {
          "name":"",//server name
          "dbVendor":"",//database type，possible values are: dbvathena,dbvazuresql,dbvbigquery,dbvcouchbase,dbvdb2,dbvgreenplum,dbvhana,dbvhive,dbvimpala,dbvinformix,dbvmdx,dbvmysqldbvnetezza,dbvopenedge,dbvoracle,dbvpostgresql,dbvpresto,dbvredshift,dbvsnowflake,dbvsparksql,dbvmssql,dbvsybase,dbvteradata,dbvvertica
          "supportsCatalogs":false,//whether there's a database layer
          "supportsSchemas":true,//whether there's a schema layer 
          "databases":[
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
          "schemas":[//schema list when there's no database object, same structure as the above servers.databases.schemas 

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

You may have found that some of the fields appear multiple times in the above json. The reason is that there are three types of database from the database/schema structure layer:

### Database who has the _database_ layer and the _schema_ layer (SQL Server for example)

The database has the _**database**_ layer and the _**schema**_ layer. `supportsCatalogs` and `supportsSchemas` will be both true.  No extra db unit field outside the database list because all units belong to the specific schema and database.

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

### Database who has the _database_ layer only (MYSQL for example)

The database has the _**database**_ layer but doesn't have the _**schema**_ layer(or no actual schema layer). `supportsCatalogs` will be true and `supportsSchemas` will be false.  No _**`schemas`**_ list under the `databases` list but extra db unit lists will be present.

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

### Database who has the schema layer only (Currently no supported database belongs to this type)

The database doesn't have the _**database**_ layer(or no actual database layer) but has the _**schema**_ layer only. `supportsCatalogs` will be false and `supportsSchemas` will be true.  No _**`databases`**_ list under the `servers` list and no extra db unit list. An extra _**`schemas`**_ list will be present directly under the `servers` list.

```json
{
    "createTime":"", //export time
    "createdBy":"sqlflow-exporter",//name of the export tool
    "physicalInstance":"",//server address
    "servers":[
        {
            "name":"",//server name
            "dbVendor":"",//database type，possible values are: dbvathena,dbvazuresql,dbvbigquery,dbvcouchbase,dbvdb2,dbvgreenplum,dbvhana,dbvhive,dbvimpala,dbvinformix,dbvmdx,dbvmysqldbvnetezza,dbvopenedge,dbvoracle,dbvpostgresql,dbvpresto,dbvredshift,dbvsnowflake,dbvsparksql,dbvmssql,dbvsybase,dbvteradata,dbvvertica
            "supportsCatalogs":false,//there's no database layer
            "supportsSchemas":true,//there's schema layer
            "schemas":[//schema list when there's no database object, same structure as the above servers.databases.schemas 
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

### Database list

Check [here](list-of-supported-dbvendors.md) to get a full database list and the type details.

### Other clarifications on the json fields:

* `$.createTime` : export time
* `$.createdBy` : name of the export tool
* `$.physicalInstance` : server address
* `$.servers[0].name` : server name
* `$.servers[0].dbVendor` : database type，possible values are: dbvathena,dbvazuresql,dbvbigquery,dbvcouchbase,dbvdb2,dbvgreenplum,dbvhana,dbvhive,dbvimpala,dbvinformix,dbvmdx,dbvmysqldbvnetezza,dbvopenedge,dbvoracle,dbvpostgresql,dbvpresto,dbvredshift,dbvsnowflake,dbvsparksql,dbvmssql,dbvsybase,dbvteradata,dbvvertica
* `$.servers[0].supportsCatalogs` : whether there's a database layer
* `$.servers[0].supportsSchemas` : whether there's a schema layer&#x20;
* `$.servers[0].databases[0].name` : database name
* `$.servers[0].databases[0].schemas[0].others` : //others, including resultset, variable, path etc
* `$.servers[0].databases[0].synonyms` : synonym list when there's no schema object, same structure as the above servers.databases.schemas.synonyms
* `$.servers[0].databases[0].sequences` : sequence list when there's no schema object, same structure as the above servers.databases.schemas.sequences
* `$.servers[0].databases[0].tables` : table list when there's no schema object, same structure as the above servers.databases.schemas.tables
* `$.servers[0].databases[0].views` : view list when there's no schema object, same structure as the above servers.databases.schemas.views
* `$.servers[0].databases[0].others` : others when there's no schema object, including resultset, variable, path etc. same structure as the above servers.databases.schemas.others
* `$.servers[0].databases[0].packages` : package list when there's no schema object, same structure as the above servers.databases.schemas.packages
* `$.servers[0].databases[0].procedures` : procedure list when there's no schema object, same structure as the above servers.databases.schemas.procedures
* `$.servers[0].databases[0].functions` : function list when there's no schema object, same structure as the above servers.databases.schemas.functions
* `$.servers[0].databases[0].triggers` : trigger list when there's no schema object, same structure as the above servers.databases.schemas.triggers
* `$.servers[0].schemas` : schema list when there's no database object, same structure as the above servers.databases.schemas
* `$.servers[0].queries` : DDL scripts in database
* `$.errorMessages` : errors during the exporting



