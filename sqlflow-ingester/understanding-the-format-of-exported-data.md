---
description: >-
  https://e.gitee.com/gudusoft/projects/151613/docs/617965/file/1485427?sub_id=6032663
---

# Understanding the format of exported data

This page gives an example and some clarifications on the format of the SQLFlow-Ingester exported data.

We may have some similar fields in the exported json data due to the fact that different databases can have various structure concepts. These similar fields won't all appear in a real case. &#x20;

Following json is a exhaustive example which lists all possible fields:

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

You may have found that some of the fields appear multiple times. The reason is that there are three types of database from the database/schema structure layer:

### Database who has the database layer and the schema layer (SQL Server for example)

The database has the database layer and the schema layer. supportsCatalogs and supportsSchemas will be both true.

### Database who has the database layer but doesn't have schema layer (MYSQL for example)

### Database who doesn't have database layer but has the schema layer (Oracle for example)

Some clarifications on the fields:

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



