# Usages

## 1. Visualize sqltext

Visualize the data lineage after analyzing the input SQL query.

* input: SQL text
* output: data lineage diagram

Find the example code under the directory:

```
└── 1\
```

<figure><img src="../.gitbook/assets/1_20221122211203.png" alt=""><figcaption></figcaption></figure>

```javascript
$(async () => {
    // get a instance of SQLFlow
    const sqlflow = await SQLFlow.init({
        container: document.getElementById('sqlflow'),
        width: 1000,
        height: 315,
        apiPrefix: 'http://xxx.com/api',
        token: '', // input your token
    });

    // set dbvendor property
    sqlflow.vendor.set('oracle');

    // set sql text property
    sqlflow.sqltext.set(`CREATE VIEW vsal 
    AS 
      SELECT a.deptno                  "Department", 
             a.num_emp / b.total_count "Employees", 
             a.sal_sum / b.total_sal   "Salary" 
      FROM   (SELECT deptno, 
                     Count()  num_emp, 
                     SUM(sal) sal_sum 
              FROM   scott.emp 
              WHERE  city = 'NYC' 
              GROUP  BY deptno) a, 
             (SELECT Count()  total_count, 
                     SUM(sal) total_sal 
              FROM   scott.emp 
              WHERE  city = 'NYC') b 
    ;`);

    sqlflow.visualize();
});

```

## **2. Visualize job**

Visualize the data lineage in a [SQLFlow Job](../1.-introduction/getting-started/different-modes-in-gudu-sqlflow/). The SQLFlow job must be already created.

* input: a SQLFlow job id, or leave it empty to view the latest job
* output: data lineage diagram

Find the example code under the directory:

```
└── 2\
```

```javascript
$(async () => {
    const sqlflow = await SQLFlow.init({
        container: document.getElementById('demo-2'),
        width: 1000,
        height: 800,
        apiPrefix: 'http://xxx.com/api',
        userId: <userId>
    });

    // view job detail by job id, or leave it empty to view the latest job
    await sqlflow.job.lineage.viewDetailById('b38273ec356d457bb98c6b3159c53be3');
});
```

<figure><img src="../.gitbook/assets/2_20221122211613.png" alt=""><figcaption></figcaption></figure>

## **3. Visualize job with hard coded parameters**

Visualize the data lineage of a specified table or column in a SQLFlow job.

* input: a SQLFlow job id, or leave it empty to view the latest job
* input: database, schema, table, column.
  * If the column is omitted, the data lineage for the specified table will be returned.
  * if the table and column are ommited, the data lineage for the specified schema will be returned.
  * if the schema, table and column are ommited, the data lineage for the specified database will be returned.
* output: data lineage diagram

Find the example code under the directory:

```
└── 3\
```

```javascript
$(async () => {
    const sqlflow = await SQLFlow.init({
        container: document.getElementById('sqlflow'),
        width: 1000,
        height: 700,
        apiPrefix: 'http://xxx.com/api',
    });

    // view job detail by job id, or leave it empty to view the latest job
    await sqlflow.job.lineage.viewDetailById('b38273ec356d457bb98c6b3159c53be3');

    sqlflow.job.lineage.selectGraph({
        database: 'DWDB', //
        schema: 'DBO',
        table: '#TMP',
        column: 'NUMBER_OFOBJECTS',
    });
});
```

## **4. Visualize job with parameters**

Visualize the data lineage of a specified table or column in a SQLFlow job.

* input: a SQLFlow job id, or leave it empty to view the latest job
* input: database, schema, table, column.
  * If the column is omitted, the data lineage for the specified table will be returned.
  * if the table and column are ommited, the data lineage for the specified schema will be returned.
  * if the schema, table and column are ommited, the data lineage for the specified database will be returned.
* output: data lineage diagram

Find the example code under the directory:

```
└── 4\
```

<figure><img src="../.gitbook/assets/3_20221122211546.png" alt=""><figcaption></figcaption></figure>

```javascript
$(async () => {
    const $jobid = $('#jobid');
    const $database = $('#database');
    const $schema = $('#schema');
    const $table = $('#table');
    const $column = $('#column');
    const $recordset = $('#recordset');
    const $function = $('#function');
    const $visualize = $('#visualize');

    const sqlflow = await SQLFlow.init({
        container: document.getElementById('sqlflow'),
        width: 1200,
        height: 800,
        apiPrefix: 'http://xxx.com/api',
        token: '', // input your token
    });

    const visualize = async () => {
        // reset default option
        $recordset.prop('checked', false);
        $function.prop('checked', false);

        // view job detail by job id, or leave it empty to view the latest job
        await sqlflow.job.lineage.viewDetailById($jobid.val());

        sqlflow.job.lineage.selectGraph({
            database: $database.val(),
            schema: $schema.val(),
            table: $table.val(),
            column: $column.val(),
        });
    };

    visualize();

    $visualize.click(visualize);

    $recordset.change(() => {
        const checked = $recordset.prop('checked');
        sqlflow.setting.showIntermediateRecordset.set(checked);
    });

    $function.change(() => {
        const checked = $function.prop('checked');
        sqlflow.setting.showFunction.set(checked);
    });
});

```

## **5. Set data lineage options of SQL query**

Generate the data lineage of a SQL query with different input parameters.

Find the example code under the directory:

```
└── 5\
```

```javascript
$(async () => {
    const $sqltext = $('#sqltext');
    const $dataflow = $('#dataflow');
    const $impact = $('#impact');
    const $args = $('#args');
    const $recordset = $('#recordset');
    const $function = $('#function');
    const $constant = $('#constant');
    const $transform = $('#transform');
    const $visualize = $('#visualize');
    const $visualizeTableLevel = $('#visualizeTableLevel');

    // get a instance of SQLFlow
    const sqlflow = await SQLFlow.init({
        container: document.getElementById('sqlflow'),
        width: 1000,
        height: 800,
        apiPrefix: 'http://xxx.com/api',
        token: '', // input your token
    });

    // set dbvendor property
    sqlflow.vendor.set('oracle');

    const visualize = async () => {
        // set sql text property
        sqlflow.sqltext.set($sqltext.val());

        // set default options
        $recordset.prop('checked', true);
        $dataflow.prop('checked', true);
        $args.prop('checked', true);
        $impact.prop('checked', false);
        $function.prop('checked', false);
        $constant.prop('checked', true);
        $transform.prop('checked', false);

        sqlflow.visualize();
    };

    visualize();

    $visualize.click(visualize);

    const visualizeTableLevel = async () => {
        // set sql text property
        sqlflow.sqltext.set($sqltext.val());
        sqlflow.visualizeTableLevel();
    };

    $visualizeTableLevel.click(visualizeTableLevel);

    $dataflow.change(() => {
        const checked = $dataflow.prop('checked');
        sqlflow.setting.dataflow.set(checked);
    });

    $impact.change(() => {
        const checked = $impact.prop('checked');
        sqlflow.setting.impact.set(checked);
    });

    $args.change(() => {
        const checked = $args.prop('checked');
        sqlflow.setting.dataflowOfAggregateFunction.set(checked);
    });

    $recordset.change(() => {
        const checked = $recordset.prop('checked');
        sqlflow.setting.showIntermediateRecordset.set(checked);
    });

    $function.change(() => {
        const checked = $function.prop('checked');
        sqlflow.setting.showFunction.set(checked);
    });

    $constant.change(() => {
        const checked = $constant.prop('checked');
        sqlflow.setting.showConstant.set(checked);
    });
    $transform.change(() => {
        const checked = $transform.prop('checked');
        sqlflow.setting.showTransform.set(checked);
    });
});

```

## **6. Visualize an embedded json object in html page**

SQLFlow will visualize the json object which contains the data lineage information and will show the actionable diagram.

Since all layout data is included in the json file, the SQLFlow widget will draw the diagram and needn't to connect to the SQLFlow backend.

So this SQLFlow widget can work without the installation of the Gudu SQLFlow.

Find the example code under the directory:

```
└── 6\
```

The format of the Json is described in [https://docs.gudusoft.com/7.-reference/lineage-model/json-format-lineage-model#id-4.-dbobjs-payload](https://docs.gudusoft.com/7.-reference/lineage-model/json-format-lineage-model#id-4.-dbobjs-payload)&#x20;

The payload is the sqlflow part of the response in the [graph interface](../3.-api-docs/sqlflow-rest-api-reference/generation-interface/sqlflow-graph.md):

<figure><img src="../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

```json
{
  "dbobjs": {
    "createdBy": "sqlflow v1.0.0",
    "servers": [
      {
        "name": "DEFAULT_SERVER",
        "dbVendor": "dbvoracle",
        "supportsCatalogs": true,
        "supportsSchemas": true,
        "databases": [
          {
            "name": "DEFAULT",
            "schemas": [
              {
                "name": "DEFAULT",
                "tables": [
                  {
                    "id": "95",
                    "name": "customers",
                    "displayName": "customers",
                    "type": "table",
                    "columns": [
                      {
                        "id": "96",
                        "name": "credit_limit",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 31,
                            "y": 21
                          },
                          {
                            "hashCode": "0",
                            "x": 31,
                            "y": 35
                          }
                        ]
                      },
                      {
                        "id": "97",
                        "name": "cust_email",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 31,
                            "y": 40
                          },
                          {
                            "hashCode": "0",
                            "x": 31,
                            "y": 52
                          }
                        ]
                      },
                      {
                        "id": "98",
                        "name": "customer_id",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 33,
                            "y": 23
                          },
                          {
                            "hashCode": "0",
                            "x": 33,
                            "y": 36
                          }
                        ]
                      }
                    ],
                    "coordinates": [
                      {
                        "hashCode": "0",
                        "x": 32,
                        "y": 16
                      },
                      {
                        "hashCode": "0",
                        "x": 32,
                        "y": 27
                      }
                    ]
                  },
                  {
                    "id": "75",
                    "name": "large_orders",
                    "displayName": "large_orders",
                    "type": "table",
                    "columns": [
                      {
                        "id": "74",
                        "name": "RelationRows",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 26,
                            "y": 8
                          },
                          {
                            "hashCode": "0",
                            "x": 26,
                            "y": 20
                          }
                        ],
                        "source": "system",
                        "uiVisible": false
                      },
                      {
                        "id": "124",
                        "name": "cem",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 31,
                            "y": 53
                          },
                          {
                            "hashCode": "0",
                            "x": 31,
                            "y": 56
                          }
                        ]
                      },
                      {
                        "id": "138",
                        "name": "cid",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 27,
                            "y": 27
                          },
                          {
                            "hashCode": "0",
                            "x": 27,
                            "y": 30
                          }
                        ]
                      },
                      {
                        "id": "123",
                        "name": "cl",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 31,
                            "y": 36
                          },
                          {
                            "hashCode": "0",
                            "x": 31,
                            "y": 38
                          }
                        ]
                      },
                      {
                        "id": "135",
                        "name": "oid",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 27,
                            "y": 11
                          },
                          {
                            "hashCode": "0",
                            "x": 27,
                            "y": 14
                          }
                        ]
                      },
                      {
                        "id": "136",
                        "name": "ottl",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 27,
                            "y": 16
                          },
                          {
                            "hashCode": "0",
                            "x": 27,
                            "y": 20
                          }
                        ]
                      },
                      {
                        "id": "137",
                        "name": "sid",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 27,
                            "y": 22
                          },
                          {
                            "hashCode": "0",
                            "x": 27,
                            "y": 25
                          }
                        ]
                      }
                    ],
                    "coordinates": [
                      {
                        "hashCode": "0",
                        "x": 26,
                        "y": 8
                      },
                      {
                        "hashCode": "0",
                        "x": 26,
                        "y": 20
                      }
                    ]
                  },
                  {
                    "id": "67",
                    "name": "medium_orders",
                    "displayName": "medium_orders",
                    "type": "table",
                    "columns": [
                      {
                        "id": "66",
                        "name": "RelationRows",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 23,
                            "y": 8
                          },
                          {
                            "hashCode": "0",
                            "x": 23,
                            "y": 21
                          }
                        ],
                        "source": "system",
                        "uiVisible": false
                      },
                      {
                        "id": "118",
                        "name": "cem",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 31,
                            "y": 53
                          },
                          {
                            "hashCode": "0",
                            "x": 31,
                            "y": 56
                          }
                        ]
                      },
                      {
                        "id": "142",
                        "name": "cid",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 24,
                            "y": 27
                          },
                          {
                            "hashCode": "0",
                            "x": 24,
                            "y": 30
                          }
                        ]
                      },
                      {
                        "id": "117",
                        "name": "cl",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 31,
                            "y": 36
                          },
                          {
                            "hashCode": "0",
                            "x": 31,
                            "y": 38
                          }
                        ]
                      },
                      {
                        "id": "139",
                        "name": "oid",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 24,
                            "y": 11
                          },
                          {
                            "hashCode": "0",
                            "x": 24,
                            "y": 14
                          }
                        ]
                      },
                      {
                        "id": "140",
                        "name": "ottl",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 24,
                            "y": 16
                          },
                          {
                            "hashCode": "0",
                            "x": 24,
                            "y": 20
                          }
                        ]
                      },
                      {
                        "id": "141",
                        "name": "sid",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 24,
                            "y": 22
                          },
                          {
                            "hashCode": "0",
                            "x": 24,
                            "y": 25
                          }
                        ]
                      }
                    ],
                    "coordinates": [
                      {
                        "hashCode": "0",
                        "x": 23,
                        "y": 8
                      },
                      {
                        "hashCode": "0",
                        "x": 23,
                        "y": 21
                      }
                    ]
                  },
                  {
                    "id": "87",
                    "name": "orders",
                    "displayName": "orders",
                    "type": "table",
                    "columns": [
                      {
                        "id": "89",
                        "name": "customer_id",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 30,
                            "y": 24
                          },
                          {
                            "hashCode": "0",
                            "x": 30,
                            "y": 37
                          }
                        ]
                      },
                      {
                        "id": "88",
                        "name": "order_id",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 30,
                            "y": 8
                          },
                          {
                            "hashCode": "0",
                            "x": 30,
                            "y": 18
                          }
                        ]
                      },
                      {
                        "id": "90",
                        "name": "order_total",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 30,
                            "y": 43
                          },
                          {
                            "hashCode": "0",
                            "x": 30,
                            "y": 56
                          }
                        ]
                      },
                      {
                        "id": "91",
                        "name": "sales_rep_id",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 31,
                            "y": 1
                          },
                          {
                            "hashCode": "0",
                            "x": 31,
                            "y": 15
                          }
                        ]
                      }
                    ],
                    "coordinates": [
                      {
                        "hashCode": "0",
                        "x": 32,
                        "y": 6
                      },
                      {
                        "hashCode": "0",
                        "x": 32,
                        "y": 14
                      }
                    ]
                  },
                  {
                    "id": "58",
                    "name": "small_orders",
                    "displayName": "small_orders",
                    "type": "table",
                    "columns": [
                      {
                        "id": "57",
                        "name": "RelationRows",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 20,
                            "y": 8
                          },
                          {
                            "hashCode": "0",
                            "x": 20,
                            "y": 20
                          }
                        ],
                        "source": "system",
                        "uiVisible": false
                      },
                      {
                        "id": "112",
                        "name": "cem",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 31,
                            "y": 53
                          },
                          {
                            "hashCode": "0",
                            "x": 31,
                            "y": 56
                          }
                        ]
                      },
                      {
                        "id": "134",
                        "name": "cid",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 21,
                            "y": 27
                          },
                          {
                            "hashCode": "0",
                            "x": 21,
                            "y": 30
                          }
                        ]
                      },
                      {
                        "id": "111",
                        "name": "cl",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 31,
                            "y": 36
                          },
                          {
                            "hashCode": "0",
                            "x": 31,
                            "y": 38
                          }
                        ]
                      },
                      {
                        "id": "131",
                        "name": "oid",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 21,
                            "y": 11
                          },
                          {
                            "hashCode": "0",
                            "x": 21,
                            "y": 14
                          }
                        ]
                      },
                      {
                        "id": "132",
                        "name": "ottl",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 21,
                            "y": 16
                          },
                          {
                            "hashCode": "0",
                            "x": 21,
                            "y": 20
                          }
                        ]
                      },
                      {
                        "id": "133",
                        "name": "sid",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 21,
                            "y": 22
                          },
                          {
                            "hashCode": "0",
                            "x": 21,
                            "y": 25
                          }
                        ]
                      }
                    ],
                    "coordinates": [
                      {
                        "hashCode": "0",
                        "x": 20,
                        "y": 8
                      },
                      {
                        "hashCode": "0",
                        "x": 20,
                        "y": 20
                      }
                    ]
                  },
                  {
                    "id": "83",
                    "name": "special_orders",
                    "displayName": "special_orders",
                    "type": "table",
                    "columns": [
                      {
                        "id": "82",
                        "name": "RelationRows",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 29,
                            "y": 8
                          },
                          {
                            "hashCode": "0",
                            "x": 29,
                            "y": 22
                          }
                        ],
                        "source": "system",
                        "uiVisible": false
                      },
                      {
                        "id": "130",
                        "name": "cem",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 31,
                            "y": 53
                          },
                          {
                            "hashCode": "0",
                            "x": 31,
                            "y": 56
                          }
                        ]
                      },
                      {
                        "id": "126",
                        "name": "cid",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 30,
                            "y": 38
                          },
                          {
                            "hashCode": "0",
                            "x": 30,
                            "y": 41
                          }
                        ]
                      },
                      {
                        "id": "129",
                        "name": "cl",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 31,
                            "y": 36
                          },
                          {
                            "hashCode": "0",
                            "x": 31,
                            "y": 38
                          }
                        ]
                      },
                      {
                        "id": "125",
                        "name": "oid",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 30,
                            "y": 19
                          },
                          {
                            "hashCode": "0",
                            "x": 30,
                            "y": 22
                          }
                        ]
                      },
                      {
                        "id": "127",
                        "name": "ottl",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 30,
                            "y": 57
                          },
                          {
                            "hashCode": "0",
                            "x": 30,
                            "y": 61
                          }
                        ]
                      },
                      {
                        "id": "128",
                        "name": "sid",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 31,
                            "y": 16
                          },
                          {
                            "hashCode": "0",
                            "x": 31,
                            "y": 19
                          }
                        ]
                      }
                    ],
                    "coordinates": [
                      {
                        "hashCode": "0",
                        "x": 29,
                        "y": 8
                      },
                      {
                        "hashCode": "0",
                        "x": 29,
                        "y": 22
                      }
                    ]
                  }
                ],
                "views": [
                  {
                    "id": "50",
                    "name": "vsal",
                    "displayName": "vsal",
                    "type": "view",
                    "columns": [
                      {
                        "id": "52",
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
                        "id": "53",
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
                        "id": "54",
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
                        "id": "49",
                        "name": "RelationRows",
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
                        "source": "system",
                        "uiVisible": false
                      }
                    ],
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
                    ]
                  }
                ],
                "others": [
                  {
                    "id": "100",
                    "name": "INSERT-SELECT-1",
                    "displayName": "INSERT-SELECT-1",
                    "type": "insert-select",
                    "columns": [
                      {
                        "id": "99",
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
                      },
                      {
                        "id": "106",
                        "name": "cem",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 31,
                            "y": 40
                          },
                          {
                            "hashCode": "0",
                            "x": 31,
                            "y": 56
                          }
                        ]
                      },
                      {
                        "id": "102",
                        "name": "cid",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 30,
                            "y": 24
                          },
                          {
                            "hashCode": "0",
                            "x": 30,
                            "y": 41
                          }
                        ]
                      },
                      {
                        "id": "105",
                        "name": "cl",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 31,
                            "y": 21
                          },
                          {
                            "hashCode": "0",
                            "x": 31,
                            "y": 38
                          }
                        ]
                      },
                      {
                        "id": "101",
                        "name": "oid",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 30,
                            "y": 8
                          },
                          {
                            "hashCode": "0",
                            "x": 30,
                            "y": 22
                          }
                        ]
                      },
                      {
                        "id": "103",
                        "name": "ottl",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 30,
                            "y": 43
                          },
                          {
                            "hashCode": "0",
                            "x": 30,
                            "y": 61
                          }
                        ]
                      },
                      {
                        "id": "104",
                        "name": "sid",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 31,
                            "y": 1
                          },
                          {
                            "hashCode": "0",
                            "x": 31,
                            "y": 19
                          }
                        ]
                      }
                    ],
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
                    ]
                  },
                  {
                    "id": "24",
                    "name": "RESULT_OF_A-1",
                    "displayName": "RESULT_OF_A-1",
                    "type": "select_list",
                    "columns": [
                      {
                        "id": "23",
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
                        "id": "25",
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
                        "id": "26",
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
                        "id": "30",
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
                    "id": "35",
                    "name": "RESULT_OF_B-1",
                    "displayName": "RESULT_OF_B-1",
                    "type": "select_list",
                    "columns": [
                      {
                        "id": "34",
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
                        "id": "36",
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
                        "id": "40",
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
                    "id": "45",
                    "name": "RS-1",
                    "displayName": "RS-1",
                    "type": "select_list",
                    "columns": [
                      {
                        "id": "46",
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
                        "id": "47",
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
                        "id": "48",
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
                        "id": "44",
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
                    "id": "22",
                    "name": "Query Create Table-1",
                    "procedureName": "batchQueries",
                    "queryHashId": "c7b73401c07136c0134ea030644be362",
                    "coordinates": [
                      {
                        "hashCode": "0",
                        "x": 42,
                        "y": 1
                      },
                      {
                        "hashCode": "0",
                        "x": 53,
                        "y": 3
                      }
                    ],
                    "uiVisible": false
                  },
                  {
                    "id": "51",
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
                  },
                  {
                    "id": "63",
                    "name": "Query Insert-1",
                    "procedureName": "batchQueries",
                    "queryHashId": "96cd680daef072c1a4c4b255d830f205",
                    "coordinates": [
                      {
                        "hashCode": "0",
                        "x": 18,
                        "y": 1
                      },
                      {
                        "hashCode": "0",
                        "x": 33,
                        "y": 37
                      }
                    ],
                    "uiVisible": false
                  }
                ]
              },
              {
                "name": "SCOTT",
                "tables": [
                  {
                    "id": "4",
                    "name": "dept",
                    "displayName": "scott.dept",
                    "type": "table",
                    "columns": [
                      {
                        "id": "5",
                        "name": "deptno",
                        "dataType": "number",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 36,
                            "y": 3
                          },
                          {
                            "hashCode": "0",
                            "x": 36,
                            "y": 9
                          }
                        ],
                        "primaryKey": true
                      },
                      {
                        "id": "6",
                        "name": "dname",
                        "dataType": "varchar2",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 37,
                            "y": 3
                          },
                          {
                            "hashCode": "0",
                            "x": 37,
                            "y": 8
                          }
                        ]
                      },
                      {
                        "id": "7",
                        "name": "loc",
                        "dataType": "varchar2",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 38,
                            "y": 3
                          },
                          {
                            "hashCode": "0",
                            "x": 38,
                            "y": 6
                          }
                        ]
                      }
                    ],
                    "coordinates": [
                      {
                        "hashCode": "0",
                        "x": 35,
                        "y": 1
                      },
                      {
                        "hashCode": "0",
                        "x": 40,
                        "y": 3
                      }
                    ]
                  },
                  {
                    "id": "11",
                    "name": "emp",
                    "displayName": "scott.emp",
                    "type": "table",
                    "columns": [
                      {
                        "id": "10",
                        "name": "RelationRows",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 42,
                            "y": 1
                          },
                          {
                            "hashCode": "0",
                            "x": 53,
                            "y": 3
                          }
                        ],
                        "source": "system",
                        "uiVisible": false
                      },
                      {
                        "id": "18",
                        "name": "comm",
                        "dataType": "number",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 49,
                            "y": 3
                          },
                          {
                            "hashCode": "0",
                            "x": 49,
                            "y": 7
                          }
                        ]
                      },
                      {
                        "id": "19",
                        "name": "deptno",
                        "dataType": "number",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 50,
                            "y": 3
                          },
                          {
                            "hashCode": "0",
                            "x": 50,
                            "y": 9
                          }
                        ],
                        "foreignKey": true
                      },
                      {
                        "id": "12",
                        "name": "empno",
                        "dataType": "number",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 43,
                            "y": 3
                          },
                          {
                            "hashCode": "0",
                            "x": 43,
                            "y": 8
                          }
                        ],
                        "primaryKey": true
                      },
                      {
                        "id": "13",
                        "name": "ename",
                        "dataType": "varchar2",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 44,
                            "y": 3
                          },
                          {
                            "hashCode": "0",
                            "x": 44,
                            "y": 8
                          }
                        ]
                      },
                      {
                        "id": "16",
                        "name": "hiredate",
                        "dataType": "date",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 47,
                            "y": 3
                          },
                          {
                            "hashCode": "0",
                            "x": 47,
                            "y": 11
                          }
                        ]
                      },
                      {
                        "id": "14",
                        "name": "job",
                        "dataType": "varchar2",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 45,
                            "y": 3
                          },
                          {
                            "hashCode": "0",
                            "x": 45,
                            "y": 6
                          }
                        ]
                      },
                      {
                        "id": "15",
                        "name": "mgr",
                        "dataType": "number",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 46,
                            "y": 3
                          },
                          {
                            "hashCode": "0",
                            "x": 46,
                            "y": 6
                          }
                        ]
                      },
                      {
                        "id": "17",
                        "name": "sal",
                        "dataType": "number",
                        "coordinates": [
                          {
                            "hashCode": "0",
                            "x": 48,
                            "y": 3
                          },
                          {
                            "hashCode": "0",
                            "x": 48,
                            "y": 6
                          }
                        ]
                      }
                    ],
                    "coordinates": [
                      {
                        "hashCode": "0",
                        "x": 42,
                        "y": 1
                      },
                      {
                        "hashCode": "0",
                        "x": 53,
                        "y": 3
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
  },
  "relationships": [
    {
      "id": "5501",
      "type": "fdd",
      "effectType": "insert",
      "target": {
        "id": "140",
        "column": "OTTL",
        "parentId": "67",
        "parentName": "MEDIUM_ORDERS",
        "coordinates": [
          {
            "hashCode": "0",
            "x": 24,
            "y": 16
          },
          {
            "hashCode": "0",
            "x": 24,
            "y": 20
          }
        ]
      },
      "sources": [
        {
          "id": "103",
          "column": "OTTL",
          "parentId": "100",
          "parentName": "INSERT-SELECT-1",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 30,
              "y": 43
            },
            {
              "hashCode": "0",
              "x": 30,
              "y": 61
            }
          ]
        }
      ],
      "processId": "63"
    },
    {
      "id": "5502",
      "type": "fdd",
      "effectType": "create_view",
      "target": {
        "id": "52",
        "column": "Department",
        "parentId": "50",
        "parentName": "VSAL",
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
      "sources": [
        {
          "id": "46",
          "column": "Department",
          "parentId": "45",
          "parentName": "RS-1",
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
        }
      ],
      "processId": "51"
    },
    {
      "id": "5503",
      "type": "fdd",
      "effectType": "insert",
      "target": {
        "id": "141",
        "column": "SID",
        "parentId": "67",
        "parentName": "MEDIUM_ORDERS",
        "coordinates": [
          {
            "hashCode": "0",
            "x": 24,
            "y": 22
          },
          {
            "hashCode": "0",
            "x": 24,
            "y": 25
          }
        ]
      },
      "sources": [
        {
          "id": "104",
          "column": "SID",
          "parentId": "100",
          "parentName": "INSERT-SELECT-1",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 31,
              "y": 1
            },
            {
              "hashCode": "0",
              "x": 31,
              "y": 19
            }
          ]
        }
      ],
      "processId": "63"
    },
    {
      "id": "5504",
      "type": "fdd",
      "effectType": "create_view",
      "target": {
        "id": "53",
        "column": "Employees",
        "parentId": "50",
        "parentName": "VSAL",
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
      "sources": [
        {
          "id": "47",
          "column": "Employees",
          "parentId": "45",
          "parentName": "RS-1",
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
        }
      ],
      "processId": "51"
    },
    {
      "id": "5505",
      "type": "fdd",
      "effectType": "insert",
      "target": {
        "id": "117",
        "column": "CL",
        "parentId": "67",
        "parentName": "MEDIUM_ORDERS",
        "coordinates": [
          {
            "hashCode": "0",
            "x": 31,
            "y": 36
          },
          {
            "hashCode": "0",
            "x": 31,
            "y": 38
          }
        ]
      },
      "sources": [
        {
          "id": "105",
          "column": "CL",
          "parentId": "100",
          "parentName": "INSERT-SELECT-1",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 31,
              "y": 21
            },
            {
              "hashCode": "0",
              "x": 31,
              "y": 38
            }
          ]
        }
      ],
      "processId": "63"
    },
    {
      "id": "5506",
      "type": "fdd",
      "effectType": "create_view",
      "target": {
        "id": "54",
        "column": "Salary",
        "parentId": "50",
        "parentName": "VSAL",
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
      "sources": [
        {
          "id": "48",
          "column": "Salary",
          "parentId": "45",
          "parentName": "RS-1",
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
        }
      ],
      "processId": "51"
    },
    {
      "id": "5507",
      "type": "fdd",
      "effectType": "insert",
      "target": {
        "id": "118",
        "column": "CEM",
        "parentId": "67",
        "parentName": "MEDIUM_ORDERS",
        "coordinates": [
          {
            "hashCode": "0",
            "x": 31,
            "y": 53
          },
          {
            "hashCode": "0",
            "x": 31,
            "y": 56
          }
        ]
      },
      "sources": [
        {
          "id": "106",
          "column": "CEM",
          "parentId": "100",
          "parentName": "INSERT-SELECT-1",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 31,
              "y": 40
            },
            {
              "hashCode": "0",
              "x": 31,
              "y": 56
            }
          ]
        }
      ],
      "processId": "63"
    },
    {
      "id": "5508",
      "type": "fdd",
      "effectType": "select",
      "target": {
        "id": "101",
        "column": "OID",
        "parentId": "100",
        "parentName": "INSERT-SELECT-1",
        "coordinates": [
          {
            "hashCode": "0",
            "x": 30,
            "y": 8
          },
          {
            "hashCode": "0",
            "x": 30,
            "y": 22
          }
        ]
      },
      "sources": [
        {
          "id": "88",
          "column": "ORDER_ID",
          "parentId": "87",
          "parentName": "ORDERS",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 30,
              "y": 8
            },
            {
              "hashCode": "0",
              "x": 30,
              "y": 18
            }
          ]
        }
      ]
    },
    {
      "id": "5509",
      "type": "fdd",
      "effectType": "select",
      "target": {
        "id": "40",
        "column": "TOTAL_SAL",
        "parentId": "35",
        "parentName": "RESULT_OF_B-1",
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
      },
      "sources": [
        {
          "id": "17",
          "column": "SAL",
          "parentId": "11",
          "parentName": "SCOTT.EMP",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 48,
              "y": 3
            },
            {
              "hashCode": "0",
              "x": 48,
              "y": 6
            }
          ]
        }
      ]
    },
    {
      "id": "5510",
      "type": "fdd",
      "effectType": "foreign_key",
      "target": {
        "id": "19",
        "column": "DEPTNO",
        "parentId": "11",
        "parentName": "SCOTT.EMP",
        "coordinates": [
          {
            "hashCode": "0",
            "x": 50,
            "y": 3
          },
          {
            "hashCode": "0",
            "x": 50,
            "y": 9
          }
        ]
      },
      "sources": [
        {
          "id": "5",
          "column": "DEPTNO",
          "parentId": "4",
          "parentName": "SCOTT.DEPT",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 36,
              "y": 3
            },
            {
              "hashCode": "0",
              "x": 36,
              "y": 9
            }
          ]
        }
      ],
      "processId": "22"
    },
    {
      "id": "5511",
      "type": "fdd",
      "effectType": "select",
      "target": {
        "id": "25",
        "column": "DEPTNO",
        "parentId": "24",
        "parentName": "RESULT_OF_A-1",
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
      "sources": [
        {
          "id": "19",
          "column": "DEPTNO",
          "parentId": "11",
          "parentName": "SCOTT.EMP",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 50,
              "y": 3
            },
            {
              "hashCode": "0",
              "x": 50,
              "y": 9
            }
          ]
        }
      ]
    },
    {
      "id": "5512",
      "type": "fdd",
      "effectType": "insert",
      "target": {
        "id": "135",
        "column": "OID",
        "parentId": "75",
        "parentName": "LARGE_ORDERS",
        "coordinates": [
          {
            "hashCode": "0",
            "x": 27,
            "y": 11
          },
          {
            "hashCode": "0",
            "x": 27,
            "y": 14
          }
        ]
      },
      "sources": [
        {
          "id": "101",
          "column": "OID",
          "parentId": "100",
          "parentName": "INSERT-SELECT-1",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 30,
              "y": 8
            },
            {
              "hashCode": "0",
              "x": 30,
              "y": 22
            }
          ]
        }
      ],
      "processId": "63"
    },
    {
      "id": "5513",
      "type": "fdd",
      "effectType": "select",
      "target": {
        "id": "102",
        "column": "CID",
        "parentId": "100",
        "parentName": "INSERT-SELECT-1",
        "coordinates": [
          {
            "hashCode": "0",
            "x": 30,
            "y": 24
          },
          {
            "hashCode": "0",
            "x": 30,
            "y": 41
          }
        ]
      },
      "sources": [
        {
          "id": "89",
          "column": "CUSTOMER_ID",
          "parentId": "87",
          "parentName": "ORDERS",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 30,
              "y": 24
            },
            {
              "hashCode": "0",
              "x": 30,
              "y": 37
            }
          ]
        }
      ]
    },
    {
      "id": "5514",
      "type": "fdd",
      "effectType": "insert",
      "target": {
        "id": "138",
        "column": "CID",
        "parentId": "75",
        "parentName": "LARGE_ORDERS",
        "coordinates": [
          {
            "hashCode": "0",
            "x": 27,
            "y": 27
          },
          {
            "hashCode": "0",
            "x": 27,
            "y": 30
          }
        ]
      },
      "sources": [
        {
          "id": "102",
          "column": "CID",
          "parentId": "100",
          "parentName": "INSERT-SELECT-1",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 30,
              "y": 24
            },
            {
              "hashCode": "0",
              "x": 30,
              "y": 41
            }
          ]
        }
      ],
      "processId": "63"
    },
    {
      "id": "5515",
      "type": "fdd",
      "effectType": "select",
      "target": {
        "id": "103",
        "column": "OTTL",
        "parentId": "100",
        "parentName": "INSERT-SELECT-1",
        "coordinates": [
          {
            "hashCode": "0",
            "x": 30,
            "y": 43
          },
          {
            "hashCode": "0",
            "x": 30,
            "y": 61
          }
        ]
      },
      "sources": [
        {
          "id": "90",
          "column": "ORDER_TOTAL",
          "parentId": "87",
          "parentName": "ORDERS",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 30,
              "y": 43
            },
            {
              "hashCode": "0",
              "x": 30,
              "y": 56
            }
          ]
        }
      ]
    },
    {
      "id": "5516",
      "type": "fdd",
      "effectType": "insert",
      "target": {
        "id": "136",
        "column": "OTTL",
        "parentId": "75",
        "parentName": "LARGE_ORDERS",
        "coordinates": [
          {
            "hashCode": "0",
            "x": 27,
            "y": 16
          },
          {
            "hashCode": "0",
            "x": 27,
            "y": 20
          }
        ]
      },
      "sources": [
        {
          "id": "103",
          "column": "OTTL",
          "parentId": "100",
          "parentName": "INSERT-SELECT-1",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 30,
              "y": 43
            },
            {
              "hashCode": "0",
              "x": 30,
              "y": 61
            }
          ]
        }
      ],
      "processId": "63"
    },
    {
      "id": "5517",
      "type": "fdd",
      "effectType": "select",
      "target": {
        "id": "104",
        "column": "SID",
        "parentId": "100",
        "parentName": "INSERT-SELECT-1",
        "coordinates": [
          {
            "hashCode": "0",
            "x": 31,
            "y": 1
          },
          {
            "hashCode": "0",
            "x": 31,
            "y": 19
          }
        ]
      },
      "sources": [
        {
          "id": "91",
          "column": "SALES_REP_ID",
          "parentId": "87",
          "parentName": "ORDERS",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 31,
              "y": 1
            },
            {
              "hashCode": "0",
              "x": 31,
              "y": 15
            }
          ]
        }
      ]
    },
    {
      "id": "5518",
      "type": "fdd",
      "effectType": "insert",
      "target": {
        "id": "137",
        "column": "SID",
        "parentId": "75",
        "parentName": "LARGE_ORDERS",
        "coordinates": [
          {
            "hashCode": "0",
            "x": 27,
            "y": 22
          },
          {
            "hashCode": "0",
            "x": 27,
            "y": 25
          }
        ]
      },
      "sources": [
        {
          "id": "104",
          "column": "SID",
          "parentId": "100",
          "parentName": "INSERT-SELECT-1",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 31,
              "y": 1
            },
            {
              "hashCode": "0",
              "x": 31,
              "y": 19
            }
          ]
        }
      ],
      "processId": "63"
    },
    {
      "id": "5519",
      "type": "fdd",
      "effectType": "select",
      "target": {
        "id": "105",
        "column": "CL",
        "parentId": "100",
        "parentName": "INSERT-SELECT-1",
        "coordinates": [
          {
            "hashCode": "0",
            "x": 31,
            "y": 21
          },
          {
            "hashCode": "0",
            "x": 31,
            "y": 38
          }
        ]
      },
      "sources": [
        {
          "id": "96",
          "column": "CREDIT_LIMIT",
          "parentId": "95",
          "parentName": "CUSTOMERS",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 31,
              "y": 21
            },
            {
              "hashCode": "0",
              "x": 31,
              "y": 35
            }
          ]
        }
      ]
    },
    {
      "id": "5520",
      "type": "fdd",
      "effectType": "insert",
      "target": {
        "id": "123",
        "column": "CL",
        "parentId": "75",
        "parentName": "LARGE_ORDERS",
        "coordinates": [
          {
            "hashCode": "0",
            "x": 31,
            "y": 36
          },
          {
            "hashCode": "0",
            "x": 31,
            "y": 38
          }
        ]
      },
      "sources": [
        {
          "id": "105",
          "column": "CL",
          "parentId": "100",
          "parentName": "INSERT-SELECT-1",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 31,
              "y": 21
            },
            {
              "hashCode": "0",
              "x": 31,
              "y": 38
            }
          ]
        }
      ],
      "processId": "63"
    },
    {
      "id": "5521",
      "type": "fdd",
      "effectType": "select",
      "target": {
        "id": "106",
        "column": "CEM",
        "parentId": "100",
        "parentName": "INSERT-SELECT-1",
        "coordinates": [
          {
            "hashCode": "0",
            "x": 31,
            "y": 40
          },
          {
            "hashCode": "0",
            "x": 31,
            "y": 56
          }
        ]
      },
      "sources": [
        {
          "id": "97",
          "column": "CUST_EMAIL",
          "parentId": "95",
          "parentName": "CUSTOMERS",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 31,
              "y": 40
            },
            {
              "hashCode": "0",
              "x": 31,
              "y": 52
            }
          ]
        }
      ]
    },
    {
      "id": "5522",
      "type": "fdd",
      "effectType": "insert",
      "target": {
        "id": "124",
        "column": "CEM",
        "parentId": "75",
        "parentName": "LARGE_ORDERS",
        "coordinates": [
          {
            "hashCode": "0",
            "x": 31,
            "y": 53
          },
          {
            "hashCode": "0",
            "x": 31,
            "y": 56
          }
        ]
      },
      "sources": [
        {
          "id": "106",
          "column": "CEM",
          "parentId": "100",
          "parentName": "INSERT-SELECT-1",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 31,
              "y": 40
            },
            {
              "hashCode": "0",
              "x": 31,
              "y": 56
            }
          ]
        }
      ],
      "processId": "63"
    },
    {
      "id": "5523",
      "type": "fdd",
      "effectType": "insert",
      "target": {
        "id": "125",
        "column": "OID",
        "parentId": "83",
        "parentName": "SPECIAL_ORDERS",
        "coordinates": [
          {
            "hashCode": "0",
            "x": 30,
            "y": 19
          },
          {
            "hashCode": "0",
            "x": 30,
            "y": 22
          }
        ]
      },
      "sources": [
        {
          "id": "101",
          "column": "OID",
          "parentId": "100",
          "parentName": "INSERT-SELECT-1",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 30,
              "y": 8
            },
            {
              "hashCode": "0",
              "x": 30,
              "y": 22
            }
          ]
        }
      ],
      "processId": "63"
    },
    {
      "id": "5524",
      "type": "fdd",
      "effectType": "select",
      "target": {
        "id": "46",
        "column": "Department",
        "parentId": "45",
        "parentName": "RS-1",
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
      "sources": [
        {
          "id": "25",
          "column": "DEPTNO",
          "parentId": "24",
          "parentName": "RESULT_OF_A-1",
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
        }
      ]
    },
    {
      "id": "5525",
      "type": "fdd",
      "effectType": "insert",
      "target": {
        "id": "131",
        "column": "OID",
        "parentId": "58",
        "parentName": "SMALL_ORDERS",
        "coordinates": [
          {
            "hashCode": "0",
            "x": 21,
            "y": 11
          },
          {
            "hashCode": "0",
            "x": 21,
            "y": 14
          }
        ]
      },
      "sources": [
        {
          "id": "101",
          "column": "OID",
          "parentId": "100",
          "parentName": "INSERT-SELECT-1",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 30,
              "y": 8
            },
            {
              "hashCode": "0",
              "x": 30,
              "y": 22
            }
          ]
        }
      ],
      "processId": "63"
    },
    {
      "id": "5526",
      "type": "fdd",
      "effectType": "insert",
      "target": {
        "id": "126",
        "column": "CID",
        "parentId": "83",
        "parentName": "SPECIAL_ORDERS",
        "coordinates": [
          {
            "hashCode": "0",
            "x": 30,
            "y": 38
          },
          {
            "hashCode": "0",
            "x": 30,
            "y": 41
          }
        ]
      },
      "sources": [
        {
          "id": "102",
          "column": "CID",
          "parentId": "100",
          "parentName": "INSERT-SELECT-1",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 30,
              "y": 24
            },
            {
              "hashCode": "0",
              "x": 30,
              "y": 41
            }
          ]
        }
      ],
      "processId": "63"
    },
    {
      "id": "5527",
      "type": "fdd",
      "effectType": "insert",
      "target": {
        "id": "134",
        "column": "CID",
        "parentId": "58",
        "parentName": "SMALL_ORDERS",
        "coordinates": [
          {
            "hashCode": "0",
            "x": 21,
            "y": 27
          },
          {
            "hashCode": "0",
            "x": 21,
            "y": 30
          }
        ]
      },
      "sources": [
        {
          "id": "102",
          "column": "CID",
          "parentId": "100",
          "parentName": "INSERT-SELECT-1",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 30,
              "y": 24
            },
            {
              "hashCode": "0",
              "x": 30,
              "y": 41
            }
          ]
        }
      ],
      "processId": "63"
    },
    {
      "id": "5528",
      "type": "fdd",
      "effectType": "select",
      "target": {
        "id": "47",
        "column": "Employees",
        "parentId": "45",
        "parentName": "RS-1",
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
      "sources": [
        {
          "id": "26",
          "column": "NUM_EMP",
          "parentId": "24",
          "parentName": "RESULT_OF_A-1",
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
          "id": "36",
          "column": "TOTAL_COUNT",
          "parentId": "35",
          "parentName": "RESULT_OF_B-1",
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
        }
      ]
    },
    {
      "id": "5529",
      "type": "fdd",
      "effectType": "insert",
      "target": {
        "id": "132",
        "column": "OTTL",
        "parentId": "58",
        "parentName": "SMALL_ORDERS",
        "coordinates": [
          {
            "hashCode": "0",
            "x": 21,
            "y": 16
          },
          {
            "hashCode": "0",
            "x": 21,
            "y": 20
          }
        ]
      },
      "sources": [
        {
          "id": "103",
          "column": "OTTL",
          "parentId": "100",
          "parentName": "INSERT-SELECT-1",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 30,
              "y": 43
            },
            {
              "hashCode": "0",
              "x": 30,
              "y": 61
            }
          ]
        }
      ],
      "processId": "63"
    },
    {
      "id": "5530",
      "type": "fdd",
      "effectType": "insert",
      "target": {
        "id": "127",
        "column": "OTTL",
        "parentId": "83",
        "parentName": "SPECIAL_ORDERS",
        "coordinates": [
          {
            "hashCode": "0",
            "x": 30,
            "y": 57
          },
          {
            "hashCode": "0",
            "x": 30,
            "y": 61
          }
        ]
      },
      "sources": [
        {
          "id": "103",
          "column": "OTTL",
          "parentId": "100",
          "parentName": "INSERT-SELECT-1",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 30,
              "y": 43
            },
            {
              "hashCode": "0",
              "x": 30,
              "y": 61
            }
          ]
        }
      ],
      "processId": "63"
    },
    {
      "id": "5531",
      "type": "fdd",
      "effectType": "insert",
      "target": {
        "id": "128",
        "column": "SID",
        "parentId": "83",
        "parentName": "SPECIAL_ORDERS",
        "coordinates": [
          {
            "hashCode": "0",
            "x": 31,
            "y": 16
          },
          {
            "hashCode": "0",
            "x": 31,
            "y": 19
          }
        ]
      },
      "sources": [
        {
          "id": "104",
          "column": "SID",
          "parentId": "100",
          "parentName": "INSERT-SELECT-1",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 31,
              "y": 1
            },
            {
              "hashCode": "0",
              "x": 31,
              "y": 19
            }
          ]
        }
      ],
      "processId": "63"
    },
    {
      "id": "5532",
      "type": "fdd",
      "effectType": "insert",
      "target": {
        "id": "133",
        "column": "SID",
        "parentId": "58",
        "parentName": "SMALL_ORDERS",
        "coordinates": [
          {
            "hashCode": "0",
            "x": 21,
            "y": 22
          },
          {
            "hashCode": "0",
            "x": 21,
            "y": 25
          }
        ]
      },
      "sources": [
        {
          "id": "104",
          "column": "SID",
          "parentId": "100",
          "parentName": "INSERT-SELECT-1",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 31,
              "y": 1
            },
            {
              "hashCode": "0",
              "x": 31,
              "y": 19
            }
          ]
        }
      ],
      "processId": "63"
    },
    {
      "id": "5533",
      "type": "fdd",
      "effectType": "insert",
      "target": {
        "id": "129",
        "column": "CL",
        "parentId": "83",
        "parentName": "SPECIAL_ORDERS",
        "coordinates": [
          {
            "hashCode": "0",
            "x": 31,
            "y": 36
          },
          {
            "hashCode": "0",
            "x": 31,
            "y": 38
          }
        ]
      },
      "sources": [
        {
          "id": "105",
          "column": "CL",
          "parentId": "100",
          "parentName": "INSERT-SELECT-1",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 31,
              "y": 21
            },
            {
              "hashCode": "0",
              "x": 31,
              "y": 38
            }
          ]
        }
      ],
      "processId": "63"
    },
    {
      "id": "5534",
      "type": "fdd",
      "effectType": "insert",
      "target": {
        "id": "111",
        "column": "CL",
        "parentId": "58",
        "parentName": "SMALL_ORDERS",
        "coordinates": [
          {
            "hashCode": "0",
            "x": 31,
            "y": 36
          },
          {
            "hashCode": "0",
            "x": 31,
            "y": 38
          }
        ]
      },
      "sources": [
        {
          "id": "105",
          "column": "CL",
          "parentId": "100",
          "parentName": "INSERT-SELECT-1",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 31,
              "y": 21
            },
            {
              "hashCode": "0",
              "x": 31,
              "y": 38
            }
          ]
        }
      ],
      "processId": "63"
    },
    {
      "id": "5535",
      "type": "fdd",
      "effectType": "insert",
      "target": {
        "id": "130",
        "column": "CEM",
        "parentId": "83",
        "parentName": "SPECIAL_ORDERS",
        "coordinates": [
          {
            "hashCode": "0",
            "x": 31,
            "y": 53
          },
          {
            "hashCode": "0",
            "x": 31,
            "y": 56
          }
        ]
      },
      "sources": [
        {
          "id": "106",
          "column": "CEM",
          "parentId": "100",
          "parentName": "INSERT-SELECT-1",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 31,
              "y": 40
            },
            {
              "hashCode": "0",
              "x": 31,
              "y": 56
            }
          ]
        }
      ],
      "processId": "63"
    },
    {
      "id": "5536",
      "type": "fdd",
      "effectType": "insert",
      "target": {
        "id": "112",
        "column": "CEM",
        "parentId": "58",
        "parentName": "SMALL_ORDERS",
        "coordinates": [
          {
            "hashCode": "0",
            "x": 31,
            "y": 53
          },
          {
            "hashCode": "0",
            "x": 31,
            "y": 56
          }
        ]
      },
      "sources": [
        {
          "id": "106",
          "column": "CEM",
          "parentId": "100",
          "parentName": "INSERT-SELECT-1",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 31,
              "y": 40
            },
            {
              "hashCode": "0",
              "x": 31,
              "y": 56
            }
          ]
        }
      ],
      "processId": "63"
    },
    {
      "id": "5537",
      "type": "fdd",
      "effectType": "select",
      "target": {
        "id": "48",
        "column": "Salary",
        "parentId": "45",
        "parentName": "RS-1",
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
      "sources": [
        {
          "id": "30",
          "column": "SAL_SUM",
          "parentId": "24",
          "parentName": "RESULT_OF_A-1",
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
        },
        {
          "id": "40",
          "column": "TOTAL_SAL",
          "parentId": "35",
          "parentName": "RESULT_OF_B-1",
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
      ]
    },
    {
      "id": "5538",
      "type": "fdd",
      "effectType": "select",
      "target": {
        "id": "30",
        "column": "SAL_SUM",
        "parentId": "24",
        "parentName": "RESULT_OF_A-1",
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
      },
      "sources": [
        {
          "id": "17",
          "column": "SAL",
          "parentId": "11",
          "parentName": "SCOTT.EMP",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 48,
              "y": 3
            },
            {
              "hashCode": "0",
              "x": 48,
              "y": 6
            }
          ]
        }
      ]
    },
    {
      "id": "5539",
      "type": "fdd",
      "effectType": "insert",
      "target": {
        "id": "139",
        "column": "OID",
        "parentId": "67",
        "parentName": "MEDIUM_ORDERS",
        "coordinates": [
          {
            "hashCode": "0",
            "x": 24,
            "y": 11
          },
          {
            "hashCode": "0",
            "x": 24,
            "y": 14
          }
        ]
      },
      "sources": [
        {
          "id": "101",
          "column": "OID",
          "parentId": "100",
          "parentName": "INSERT-SELECT-1",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 30,
              "y": 8
            },
            {
              "hashCode": "0",
              "x": 30,
              "y": 22
            }
          ]
        }
      ],
      "processId": "63"
    },
    {
      "id": "5540",
      "type": "fdd",
      "effectType": "insert",
      "target": {
        "id": "142",
        "column": "CID",
        "parentId": "67",
        "parentName": "MEDIUM_ORDERS",
        "coordinates": [
          {
            "hashCode": "0",
            "x": 24,
            "y": 27
          },
          {
            "hashCode": "0",
            "x": 24,
            "y": 30
          }
        ]
      },
      "sources": [
        {
          "id": "102",
          "column": "CID",
          "parentId": "100",
          "parentName": "INSERT-SELECT-1",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 30,
              "y": 24
            },
            {
              "hashCode": "0",
              "x": 30,
              "y": 41
            }
          ]
        }
      ],
      "processId": "63"
    }
  ],
  "processes": [
    {
      "id": "22",
      "name": "Query Create Table-1",
      "procedureName": "batchQueries",
      "queryHashId": "c7b73401c07136c0134ea030644be362",
      "type": "sstcreatetable",
      "coordinates": [
        {
          "hashCode": "0",
          "x": 42,
          "y": 1
        },
        {
          "hashCode": "0",
          "x": 53,
          "y": 3
        }
      ],
      "uiVisible": false
    },
    {
      "id": "51",
      "name": "Query Create View-1",
      "procedureName": "batchQueries",
      "queryHashId": "4ef278b9a7850f717990e96aae7a3f43",
      "type": "sstcreateview",
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
    },
    {
      "id": "63",
      "name": "Query Insert-1",
      "procedureName": "batchQueries",
      "queryHashId": "96cd680daef072c1a4c4b255d830f205",
      "type": "sstinsert",
      "coordinates": [
        {
          "hashCode": "0",
          "x": 18,
          "y": 1
        },
        {
          "hashCode": "0",
          "x": 33,
          "y": 37
        }
      ],
      "uiVisible": false
    }
  ]
}
```

And giving that value to the widget:

<figure><img src="../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

## **7. Visualize data lineage in a separate json file**

Read and visualize the data lineage in a json file. This json file should be accessable in the same server as the SQLFlow widget.

Since all layout data is included in the json file, the SQLFlow widget will generate the diagram and needn't to connect to the SQLFlow backend.

This SQLFlow widget can work without the installation of the Gudu SQLFlow.

Find the example code under the directory:

```
└── 7\
```

## **8. Get error message**

Getting error message after processing input SQL qurey.

Find the example code under the directory:

```
└── 8\
```

<figure><img src="../.gitbook/assets/8_20221122211806.png" alt=""><figcaption></figcaption></figure>

```javascript
$(async () => {
    const $sqltext = $('#sqltext');
    const $visualize = $('#visualize');
    const $error = $('#error');

    // get a instance of SQLFlow
    const sqlflow = await SQLFlow.init({
        container: document.getElementById('sqlflow'),
        width: 1000,
        height: 400,
        apiPrefix: 'http://xxx.com/api',
        token: '', // input your token
    });

    // set dbvendor property
    sqlflow.vendor.set('oracle');

    const visualize = async () => {
        // set sql text property
        sqlflow.sqltext.set($sqltext.val());

        await sqlflow.visualize();

        const error = sqlflow.error.get();
        if (error && error.length > 0) {
            console.log(sqlflow.error.get());
            let text = '';
            error.forEach(item => {
                text += `${item.errorType} : ${item.errorMessage}`;
            });
            $error.val(text);
        } else {
            $error.val('');
        }
    };

    visualize();

    $visualize.click(visualize);
});

```

## **9. Event: add an event listener on field(column) click**

Add an event listener on field(column) click so that you can get detailed information about the field(column) that been clicked.

Find the example code under the directory:

```
└── 9\
```

<figure><img src="../.gitbook/assets/9_20221122211912.png" alt=""><figcaption></figcaption></figure>

```javascript
$(async () => {
    const $sqltext = $('#sqltext');
    const $visualize = $('#visualize');
    const $message = $('#message');

    // get a instance of SQLFlow
    const sqlflow = await SQLFlow.init({
        container: document.getElementById('sqlflow'),
        width: 1000,
        height: 400,
        apiPrefix: 'http://xxx.com/api',
        token: '', // input your token
    });

    // set dbvendor property
    sqlflow.vendor.set('oracle');

    // add an event listener on field(column) click
    sqlflow.addEventListener('onFieldClick', field => {
        $message.val(JSON.stringify(field));

        // remove all event listeners
        // sqlflow.removeAllEventListener()
    });

    const visualize = async () => {
        // set sql text property
        sqlflow.sqltext.set($sqltext.val());

        await sqlflow.visualize();
    };

    visualize();

    $visualize.click(visualize);
});

```

## **12. Access data lineage from url**

User can directly access the data lineage through an url by specifying the data lineage type, table and column.

> All data lineages come from the default job at the Gudu SQLFlow backend. If no default job is set, the lineage data will be retrieved from the latest job.

```
http://127.0.0.1/widget/12/?type=upstream&table=dbo.emp
http://127.0.0.1/widget/12/?type=upstream&table=dbo.emp&column=salary
```

### Input parameters

* type: upstream or downstream
* table
* column: if column is omitted, return the lineage for table
* stopat: value in regex expression, the lineage(upstream or downstream) stops at the given table if this input is set

the table and column name in the url is case insensitive.

#### stopat with regex expression

? The question mark indicates _zero or one_ occurrences of the preceding element. For example,`colou?r` matches both "color" and "colour". The question mark equals to {0, 1}

\* The asterisk indicates _zero or more_ occurrences of the preceding element. For example,`ab*c` matches "ac", "abc", "abbc", "abbbc", and so on. The asterisk equals to {0,}

\+ The plus sign indicates _one or more_ occurrences of the preceding element. For example,`ab+c` matches "abc", "abbc", "abbbc", and so on, but not "ac".

Regular expression has two matching modes: `matches` and `find`.

`matches` are all exact matches, `find` is a partial match. SQLFlow uses `matches` mode.

**Example:**

To match `mio.public.usecase_na_mio004_infohubview006` with base string `mio.public.usecase_na_mio004_infohub`

The regex expression should be: `mio.public.usecase_na_mio004_infohub.*`

![](https://foruda.gitee.com/images/1676387254568489058/34f24b0f_1228015.png)

`.` matches any single character, \* matches the preceding element zero or more times(in this case, it can be any character).

we cannot use `mio.public.usecase_na_mio004_infohub.？` to match because `?` indicates only zero or one occurrences of the preceding element, it is not a exact match:

![](https://foruda.gitee.com/images/1676387786494834978/5084551f_1228015.png)

**Use Regex Expression in stopat:**

http://127.0.0.1/widget/12/?type=downstream&\&table=MIO.PUBLIC.XXX&\&column=fact\_guid

<figure><img src="../.gitbook/assets/微信截图_20230218223016.png" alt=""><figcaption></figcaption></figure>

http://127.0.0.1/widget/12/?type=downstream\&table=MIO.PUBLIC.XXX\&column=fact\_guid\&stopat=mio.public.usecase.\*

<figure><img src="../.gitbook/assets/微信截图_20230218222916.png" alt=""><figcaption></figcaption></figure>

Find the example code under the directory:

```
└── 12\
```

## **13. Visualize a csv file that includes lineage data**

The format of the csv:

```csv
source_db,source_schema,source_table,source_column,target_db,target_schema,target_table,target_column,relation_type,effect_type
D1E9IQ1AE488E4,DBT_TESTS,STG_PAYMENTS,AMOUNT,DEFAULT,DEFAULT,RS-5,COUPON_AMOUNT,fdd,select
D1E9IQ1AE488E4,DBT_TESTS,STG_ORDERS,ORDER_ID,DEFAULT,DEFAULT,RS-5,ORDER_ID,fdd,select
D1E9IQ1AE488E4,DBT_TESTS,STG_ORDERS,STATUS,DEFAULT,DEFAULT,RS-5,STATUS,fdd,select
D1E9IQ1AE488E4,DBT_TESTS,STG_PAYMENTS,AMOUNT,DEFAULT,DEFAULT,RS-5,CREDIT_CARD_AMOUNT,fdd,select
D1E9IQ1AE488E4,DBT_TESTS,STG_PAYMENTS,AMOUNT,DEFAULT,DEFAULT,RS-5,GIFT_CARD_AMOUNT,fdd,select
D1E9IQ1AE488E4,DBT_TESTS,STG_ORDERS,ORDER_DATE,DEFAULT,DEFAULT,RS-5,ORDER_DATE,fdd,select
D1E9IQ1AE488E4,DBT_TESTS,STG_PAYMENTS,AMOUNT,DEFAULT,DEFAULT,RS-5,AMOUNT,fdd,select
D1E9IQ1AE488E4,DBT_TESTS,STG_ORDERS,CUSTOMER_ID,DEFAULT,DEFAULT,RS-5,CUSTOMER_ID,fdd,select
D1E9IQ1AE488E4,DBT_TESTS,STG_PAYMENTS,AMOUNT,DEFAULT,DEFAULT,RS-5,BANK_TRANSFER_AMOUNT,fdd,select
```

All necessary files are under this directory.

```
└── 13\
```

<figure><img src="../.gitbook/assets/13_20221122212229.png" alt=""><figcaption></figcaption></figure>

```javascript
$(async () => {
    const $sqltext = $('#sqltext');
    const $dataflow = $('#dataflow');
    const $impact = $('#impact');
    const $recordset = $('#recordset');
    const $function = $('#function');
    const $visualize = $('#visualize');
    const $file = $('#file');

    // get a instance of SQLFlow
    const sqlflow = await SQLFlow.init({
        container: document.getElementById('sqlflow'),
        width: 1000,
        height: 800,
        apiPrefix: 'http://xxx.com/api',
        token: '', // input your token
    });

    // set dbvendor property
    sqlflow.vendor.set('oracle');

    const visualize = async () => {
        // set sql text property
        sqlflow.sqltext.set($sqltext.val());

        // set default options
        $recordset.prop('checked', true);
        $dataflow.prop('checked', true);
        $impact.prop('checked', false);
        $function.prop('checked', false);

        sqlflow.visualize();
    };

    $file.on('change', async e => {
        const file = $file.prop('files')[0];
        const content = await file.text();
        $sqltext.val(content);
        visualize();
    });

    $visualize.click(visualize);

    $dataflow.change(() => {
        const checked = $dataflow.prop('checked');
        sqlflow.setting.dataflow.set(checked);
    });

    $impact.change(() => {
        const checked = $impact.prop('checked');
        sqlflow.setting.impact.set(checked);
    });

    $recordset.change(() => {
        const checked = $recordset.prop('checked');
        sqlflow.setting.showIntermediateRecordset.set(checked);
    });

    $function.change(() => {
        const checked = $function.prop('checked');
        sqlflow.setting.showFunction.set(checked);
    });
});

```

## **14. Visualize the lineage data using Vue**

SQLFlow Widget provides a Vue library to support Vue framework.

Find the example code under the directory:

```
└── 14\
```

```javascript
document.addEventListener('DOMContentLoaded', async () => {
    Vue.component('sqlflow', {
        template: '<div ref="el"></div>',

        async mounted() {
            // get a instance of SQLFlow
            const sqlflow = await SQLFlow.init({
                container: this.$refs.el, // get element ref from vue
                width: 1000,
                height: 315,
                apiPrefix: 'http://xxx.com/api',
                token: '', // input your token
            });

            // set dbvendor property
            sqlflow.vendor.set('oracle');

            // set sql text property
            sqlflow.sqltext.set(`CREATE VIEW vsal
                    AS
                      SELECT a.deptno                  "Department",
                             a.num_emp / b.total_count "Employees",
                             a.sal_sum / b.total_sal   "Salary"
                      FROM   (SELECT deptno,
                                     Count()  num_emp,
                                     SUM(sal) sal_sum
                              FROM   scott.emp
                              WHERE  city = 'NYC'
                              GROUP  BY deptno) a,
                             (SELECT Count()  total_count,
                                     SUM(sal) total_sal
                              FROM   scott.emp
                              WHERE  city = 'NYC') b
                    ;`);

            sqlflow.visualize();
        },
    });

    var app = new Vue({
        el: '#sqlflow',
        template: '<sqlflow />',
    });
});

```

## **15. Event: add an event listener on table click**

Add an event listener on table click so that you can get detailed information about the table which is clicked.

Find the example code under the directory:

```
└── 15\
```

<figure><img src="../.gitbook/assets/15_20221122212036 (1).png" alt=""><figcaption></figcaption></figure>

```javascript
$(async () => {
    const $sqltext = $('#sqltext');
    const $visualize = $('#visualize');
    const $message = $('#message');

    // get a instance of SQLFlow
    const sqlflow = await SQLFlow.init({
        container: document.getElementById('sqlflow'),
        width: 1000,
        height: 400,
        apiPrefix: 'http://xxx.com/api',
        token: '', // input your token
    });

    // set dbvendor property
    sqlflow.vendor.set('oracle');

    // add an event listener on table click
    sqlflow.addEventListener('onTableNameClick', table => {
        $message.val(JSON.stringify(table));

        // remove all event listeners
        // sqlflow.removeAllEventListener()
    });

    const visualize = async () => {
        // set sql text property
        sqlflow.sqltext.set($sqltext.val());

        await sqlflow.visualize();
    };

    visualize();

    $visualize.click(visualize);
});

```

