---
description: >-
  https://e.gitee.com/gudusoft/projects/151613/docs/617965/file/1485427?sub_id=6032659
---

# Data lineage format reference

This page gives a detail reference of the data lineage response format which is returned on [SQLFlow UI](../../introduction/ui/).  The SQLFlow UI gets result from the /sqlflow/generation/sqlflow/graph endpoint and having following elements:

### 1. Top level elements

```json
{
	"code": 200,
	"data": {
		"mode": "global",
		"summary": {
		},
		"sqlflow": {
		},
		"graph": {
		}
	},
	"sessionId": "3bf4a61f5d41a016d0f91f28c2c1791d7100e1c159c31dab4e1f3bce603afd1c_1663684880303",
  	"jobId": "JobId",  
	"error": "error msgs",
}
```

* code: Http Status code, 200 for OK. 4XX **** for cases in which the client seems to have erred such as no authorization or bad request. 500 for internal server error. Error messages would be present in _`error`_ If the code is not 200 (request is not a success).
* data: data payload
  * mode: data mode. Could be _`global`_ or _`summary`_. Will be set to _ `summary` _ mode when the relation number exceeds the _`relation_limit`_
    * _`global`_ show all data
    * _`summary`_ only share the statics information and there's no graph information. No field data in the table and only table info. Users need to invoke [REST Api](../../api-docs/sqlflow-rest-api-reference/) to get the field data in detail.
  * [summary](data-lineage-format-reference.md#2.-summary-payload): payload for statics information in _`summary`_ mode
  * [sqlflow](data-lineage-format-reference.md#undefined): data model of the analysis result
  * [graph](data-lineage-format-reference.md#undefined): graph model of the analysis result
* sessionId: session id, used to get the cache information in [Query mode](../../introduction/getting-started/different-modes-in-gudu-sqlflow/query-mode.md)
* jobId: job id, used to get the cache informaion in [Job mode](../../introduction/getting-started/different-modes-in-gudu-sqlflow/job-mode.md)
* error: contains error messages if the status code is not 200

### 2. Summary payload

```json
"summary": {
	"schema": 1,
	"process": 2,
	"database": 0,
	"view": 1,
	"mostRelationTables": [{
		"table": "SMALL_ORDERS"
	}, {
		"table": "MEDIUM_ORDERS"
	}, {
		"table": "LARGE_ORDERS"
	}],
	"column": 43,
	"relationship": 41,
	"table": 7
}
```

* database: database number
* schema: schema number
* table: table number
* view: view number
* column: column number
* relationship: relationship number
* process: process number
* mostRelationTables: the top three tables which contain the most relationships

### 3. Sqlflow payload

```json
"sqlflow": {
	"dbobjs": {
		"createdBy": "grabit v1.7.0",
		"servers": [{}]
	},
	"relationships": [{}]
}
```

sqlflow payload contains two nodes. dbojbs and relationship.

* [dbojbs](data-lineage-format-reference.md#4.-dbobjs-payload): metadata, contains information of instance, db, schema, table, view, storage procedure, function, trigger, dblink, sequence, ddl etc..
* [relationships](data-lineage-format-reference.md#3.-relationship-payload): relationships after analyzing sql

### 4. Dbobjs payload

```json
{
    "servers": [{
            "dbVendor": "dbvoracle",
            "name": "\"ORCLPDB1.LOCALDOMAIN\"",
            "supportsCatalogs": false,
            "supportsSchemas": true,
            "schemas": [{
                "name": "OE",
                "tables": [{
                    "columns": [{
                        "name": "ORDER_ID",
                        "id": "57"
                    }],
                    "id": "56",
                    "name": "ORDERS",
                    "type": "table"
                }],
                "packages": [{
                    "id": "26",
                    "name": "package1",
                    "procedures": [{
                        "name": "procedure1",
                        "type": "procedure"
                    }]
                }, {
                    "id": "42",
                    "name": "package2",
                    "procedures": [{
                        "name": "procedure1",
                        "type": "procedure"
                    }]
                }]
            }]
        },
        {
            "name": "default_server",
            "dbVendor": "dbvmysql",
            "supportsCatalogs": true,
            "supportsSchemas": false,
            "databases": [{
                "name": "DEFAULT",
                "tables": [{
                    "columns": [{
                        "name": "field9",
                        "id": "110"
                    }, {
                        "name": "field1",
                        "id": "111"
                    }, {
                        "name": "field5",
                        "id": "116"
                    }],
                    "id": "96",
                    "name": "table1",
                    "type": "table"
                }]
            }]
        }, {
            "dbVendor": "dbvmssql",
            "name": "default_server",
            "supportsCatalogs": true,
            "supportsSchemas": true,
            "databases": [{
                "name": "DEFAULT",
                "schemas": [{
                    "name": "HumanResources",
                    "tables": [{
                        "columns": [{
                            "name": "BusinessEntityID",
                            "id": "13"
                        }, {
                            "name": "HireDate",
                            "id": "14"
                        }],
                        "id": "12",
                        "name": "Employee",
                        "type": "table"
                    }]
                }]
            }]
        }
    ]
}

```

The top element of the dbobjs payload is an array and the array representing different server instances. For each server instance, we will have:

1. dbVendor: database type
2. name: instance name
3. supportsCatalogs: whether support database (check [here](https://docs.gudusoft.com/sqlflow-ingester/understanding-the-format-of-exported-data#database-who-has-the-database-layer-and-the-schema-layer-sql-server-for-example) for more details on this flag)
4. supportsSchemas: whether support schema (check [here](https://docs.gudusoft.com/sqlflow-ingester/understanding-the-format-of-exported-data#database-who-has-the-database-layer-and-the-schema-layer-sql-server-for-example) for more details on this flag)
5. databases: present if support database
6. schemas: present if database is not supported and only schema is supported. Type of the schema could be _`oracle`_ or _`db2`_
7. dbLinks: dbLinks will be present if the resposne json is generated from metadata. Will not be present If the response json is generated from dataflow
8. queries: present if the response json is generated from metadata&#x20;

There are tree types for the server instance (same logic [here](../../sqlflow-ingester/understanding-the-format-of-exported-data.md)):

1. if supportsCatalogs=true,supportsSchemas=true:
   * server-->database-->schema-->tables/views/others/packages/procedures/functions/triggers
2. if supportsCatalogs=true,supportsSchemas=false:
   * server-->database-->tables/views/others/packages/procedures/functions/triggers
3. if supportsCatalogs = false, supportsSchemas = true:
   * server --> schema --> tables/views/others/packages/procedures/functions/triggers

Schema may contain other information indicating the data of _`procedure`_, _`trigger`_, _`function`_

```json
"others": [
    {
        "id": "85",
        "name": "INSERT-SELECT-1",
        "type": "insert-select",
        "columns": [
            {
                "id": "84",
                "name": "RelationRows",
                "coordinates": [
                    {
                        "hashCode": "0",
                        "x": 30,
                        "y": 8
                    },
                    {
                        "hashCode": "0",
                        "x": 31,
                        "y": 56
                    }
                ],
                "source": "system",
                "uiVisible": false
            }, ...
    ]
```

### 5. Relationship payload

Relationship is the atom unit of the data lineage. Relationship builds a link between the source and target column (column-level lineage).

A relation includes the `type`, `target`, `sources` and other attributes.

```json
"relationships": [{
	"id": "56",
	"type": "fdd",
	"effectType": "insert",
	"target": {
		"id": "102",
		"column": "CL",
		"parentId": "52",
		"parentName": "MEDIUM_ORDERS",
		"coordinates": [{
			"hashCode": "0",
			"x": 31,
			"y": 36
		}, {
			"hashCode": "0",
			"x": 31,
			"y": 38
		}]
	},
	"sources": [{
		"id": "90",
		"column": "CL",
		"parentId": "85",
		"parentName": "INSERT-SELECT-1",
		"coordinates": [{
			"hashCode": "0",
			"x": 31,
			"y": 21
		}, {
			"hashCode": "0",
			"x": 31,
			"y": 38
		}]
	}],
	"processId": "48"
}]

```

* id: relation id
* type: relation type, could be _`fdd`_, _`fdr`_, _`join`_, or _`call`_
* function: present if the relationship is about function
* effectType: effect type of the relation, based on STMT
* target: relation target, of [RelationshipElement](data-lineage-format-reference.md#relationshipelement) structure
* sources: relation sources, belongs to [RelationshipElement](data-lineage-format-reference.md#relationshipelement) structure
* caller: caller if the type is _`call`_,  belongs to [RelationshipElement](data-lineage-format-reference.md#relationshipelement) structure
* callees: callees if the type is _`call`_, is an array of  [RelationshipElement](data-lineage-format-reference.md#relationshipelement) objects
* processId: process id by which the relation is generated
* timestampMin: the earliest time when the relationship is generated
* timestampMax: the latest time when the relationship is generated

#### RelationshipElement

* id
* name
* column
* columnType
* sourceId
* sourceName
* transforms: array of [Transform](data-lineage-format-reference.md#transform)
* parentId
* parentName
* clauseType
* function
* type
* coordinates

#### Transform&#x20;

* type
* code
* coordinates

### 6. Graph payload

```json
"graph": {
    "relationshipIdMap": {
        "e0": ["5519", "fdd"],
    },
    "elements": {
        "tables": [{
            "columns": [{
                "height": 16.0,
                "id": "n0::n0",
                "label": {
                    "content": "oid",
                    "fontFamily": "Segoe UI Symbol",
                    "fontSize": "12",
                    "height": 13.96875,
                    "width": 35.0,
                    "x": 0.0,
                    "y": 0.0
                },
                "width": 160.0,
                "x": 575.0,
                "y": -565.9073
            }],
	    "id": "n4",
	    "label": {
		"content": "customers",
		"fontFamily": "Segoe UI Symbol",
		"fontSize": "12",
		"height": 17.96875,
		"width": 162.0,
		"x": 0.0,
		"y": 0.0
	    },
	    "width": 162.0,
	    "height": 57.96875,
        }],
        "edges": [{
            "id": "e0",
            "sourceId": "n9::n5",
            "targetId": "n5::n5"
        }
    },
    "tooltip": {},
    "listIdMap": {
        "n0": ["68"],
        "n0::n0": ["110"],
    }
}
```

* relationIdMap:
  * Mapping list between the graph ui id and the relationship id
* listIdMap:
  * Mapping list between graph ui id and the graph model id&#x20;
* elements:
  * tables
    * id: table id, will be generated into UI model by mappings in the listIdMap
    * table: table name
    * width: table width
    * height: table height
    * x：table x-axis (horizontal) coordinate
    * y：table y-axis (vertical) coordinate
    * columns
      * id: columns id, will be generated into UI model by mappings in the listIdMap
      * x：column x-axis (horizontal) coordinate
      * y：column y-axis (vertical) coordinate
  * edges
    * id: edge id, mapped with relationship id and type through relationIdMap
    * sourceId: source column id
    * targetId: target column id

### Dataflow.xml Structure

{% content-ref url="../../introduction/java-library/usage/dataflow.xml-structure.md" %}
[dataflow.xml-structure.md](../../introduction/java-library/usage/dataflow.xml-structure.md)
{% endcontent-ref %}
