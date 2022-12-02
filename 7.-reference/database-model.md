# Database Model

The database model will be generated when we read data from the database. The database model is similar to the lineage model and it contains extra db info.

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

The object under the `server` block is same as [Dbobjs](lineage-model/json-format-lineage-model.md#4.-dbobjs-payload) in linage model. Check [Dbobjs](lineage-model/json-format-lineage-model.md#4.-dbobjs-payload) to understand more on this field. Apart from the `server` block, check following table for more details:

| Field name       | Description                                                                        |
| ---------------- | ---------------------------------------------------------------------------------- |
| createTime       | database model export time, usually it can be the time you execute the exportation |
| createdBy        | <p>name of the export tool<br>sqlflow-ingester v1.1.8 for example</p>              |
| physicalInstance | <p>your server address,<br>106.54.xx.xx for example</p>                            |
| errorMessages    | errors during the exporting                                                        |
