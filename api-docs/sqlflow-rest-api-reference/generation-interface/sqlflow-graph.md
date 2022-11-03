# /sqlflow/generation/sqlflow/graph

{% swagger src="../../../.gitbook/assets/swagger.yaml" path="/sqlflow/generation/sqlflow/graph" method="post" %}
[swagger.yaml](../../../.gitbook/assets/swagger.yaml)
{% endswagger %}

```json
{
  "code": 200,
  "data": {
    "mode": "global",
    "summary": {
      "schema": 0,
      "process": 0,
      "database": 0,
      "view": 0,
      "mostRelationTables": [
        {
          "table": "EMP"
        },
        {
          "table": "DEPT"
        }
      ],
      "column": 4,
      "relationship": 1,
      "table": 3
    },
    "sqlflow": {
      "dbvendor": "dbvoracle",
      "dbobjs": [
        {
          "id": "4",
          "name": "EMP",
          "type": "table",
          "columns": [
            {
              "id": "5",
              "name": "DEPTID",
              "coordinates": [
                {
                  "x": 1,
                  "y": 35,
                  "hashCode": "0"
                },
                {
                  "x": 1,
                  "y": 45,
                  "hashCode": "0"
                }
              ]
            },
            {
              "id": "17",
              "name": "ENAME",
              "coordinates": [
                {
                  "x": 1,
                  "y": 8,
                  "hashCode": "0"
                },
                {
                  "x": 1,
                  "y": 13,
                  "hashCode": "0"
                }
              ]
            }
          ],
          "coordinates": [
            {
              "x": 1,
              "y": 19,
              "hashCode": "0"
            },
            {
              "x": 1,
              "y": 22,
              "hashCode": "0"
            }
          ]
        },
        {
          "id": "9",
          "name": "DEPT",
          "type": "table",
          "columns": [
            {
              "id": "10",
              "name": "ID",
              "coordinates": [
                {
                  "x": 1,
                  "y": 48,
                  "hashCode": "0"
                },
                {
                  "x": 1,
                  "y": 55,
                  "hashCode": "0"
                }
              ]
            }
          ],
          "coordinates": [
            {
              "x": 1,
              "y": 24,
              "hashCode": "0"
            },
            {
              "x": 1,
              "y": 28,
              "hashCode": "0"
            }
          ]
        },
        {
          "id": "15",
          "name": "PSEUDO_TABLE_INCLUDE_ORPHAN_COLUMN",
          "type": "pseudoTable",
          "columns": [
            {
              "id": "16",
              "name": "ENAME",
              "coordinates": [
                {
                  "x": 1,
                  "y": 8,
                  "hashCode": "0"
                },
                {
                  "x": 1,
                  "y": 13,
                  "hashCode": "0"
                }
              ]
            }
          ],
          "coordinates": [
            {
              "x": 1,
              "y": 1,
              "hashCode": "0"
            },
            {
              "x": 1,
              "y": 35,
              "hashCode": "0"
            }
          ]
        },
        {
          "id": "12",
          "name": "RS-1",
          "type": "select_list",
          "columns": [
            {
              "id": "13",
              "name": "ENAME",
              "coordinates": [
                {
                  "x": 1,
                  "y": 8,
                  "hashCode": "0"
                },
                {
                  "x": 1,
                  "y": 13,
                  "hashCode": "0"
                }
              ]
            },
            {
              "id": "11",
              "name": "RELATIONROWS",
              "coordinates": [
                {
                  "x": 1,
                  "y": 8,
                  "hashCode": "0"
                },
                {
                  "x": 1,
                  "y": 13,
                  "hashCode": "0"
                }
              ],
              "source": "SYSTEM"
            }
          ],
          "coordinates": [
            {
              "x": 1,
              "y": 8,
              "hashCode": "0"
            },
            {
              "x": 1,
              "y": 13,
              "hashCode": "0"
            }
          ]
        }
      ],
      "relationships": [
        {
          "id": "1",
          "type": "fdd",
          "effectType": "select",
          "target": {
            "id": "13",
            "column": "ENAME",
            "parentId": "12",
            "parentName": "RS-1",
            "coordinates": [
              {
                "x": 1,
                "y": 8,
                "hashCode": "0"
              },
              {
                "x": 1,
                "y": 13,
                "hashCode": "0"
              }
            ]
          },
          "sources": [
            {
              "id": "17",
              "column": "ENAME",
              "parentId": "4",
              "parentName": "EMP",
              "coordinates": [
                {
                  "x": 1,
                  "y": 8,
                  "hashCode": "0"
                },
                {
                  "x": 1,
                  "y": 13,
                  "hashCode": "0"
                }
              ]
            }
          ]
        },
        {
          "id": "2",
          "type": "fdr",
          "effectType": "select",
          "target": {
            "id": "11",
            "column": "RELATIONROWS",
            "parentId": "12",
            "parentName": "RS-1",
            "coordinates": [
              {
                "x": 1,
                "y": 8,
                "hashCode": "0"
              },
              {
                "x": 1,
                "y": 13,
                "hashCode": "0"
              }
            ]
          },
          "sources": [
            {
              "id": "5",
              "column": "DEPTID",
              "parentId": "4",
              "parentName": "EMP",
              "clauseType": "where",
              "coordinates": [
                {
                  "x": 1,
                  "y": 35,
                  "hashCode": "0"
                },
                {
                  "x": 1,
                  "y": 45,
                  "hashCode": "0"
                }
              ]
            },
            {
              "id": "10",
              "column": "ID",
              "parentId": "9",
              "parentName": "DEPT",
              "clauseType": "where",
              "coordinates": [
                {
                  "x": 1,
                  "y": 48,
                  "hashCode": "0"
                },
                {
                  "x": 1,
                  "y": 55,
                  "hashCode": "0"
                }
              ]
            }
          ]
        }
      ],
      "errors": [
        {
          "errorMessage": "find orphan column(10500) near: ename(1,8)",
          "errorType": "SyntaxHint",
          "coordinates": [
            {
              "x": 1,
              "y": 8,
              "hashCode": "0"
            },
            {
              "x": 1,
              "y": 13,
              "hashCode": "0"
            }
          ]
        },
        {
          "errorMessage": "Link orphan column [ename] to the first table [emp]",
          "errorType": "LinkOrphanColumn",
          "coordinates": [
            {
              "x": 1,
              "y": 8,
              "hashCode": "0"
            },
            {
              "x": 1,
              "y": 13,
              "hashCode": "0"
            }
          ]
        }
      ]
    },
    "graph": {
      "relationshipIdMap": {
        "e0": [
          "1",
          "fdd"
        ]
      },
      "elements": {
        "tables": [
          {
            "columns": [
              {
                "height": 16,
                "id": "n0::n0",
                "label": {
                  "content": "ename",
                  "fontFamily": "Segoe UI Symbol",
                  "fontSize": "12",
                  "height": 13.96875,
                  "width": 59,
                  "x": 0,
                  "y": 0
                },
                "width": 160,
                "x": 213,
                "y": -30.000149
              }
            ],
            "height": 41.96875,
            "id": "n0",
            "label": {
              "content": "RS-1",
              "fontFamily": "Segoe UI Symbol",
              "fontSize": "12",
              "height": 17.96875,
              "width": 162,
              "x": 0,
              "y": 0
            },
            "width": 162,
            "x": 212,
            "y": -51.9689
          },
          {
            "columns": [
              {
                "height": 16,
                "id": "n1::n0",
                "label": {
                  "content": "ename",
                  "fontFamily": "Segoe UI Symbol",
                  "fontSize": "12",
                  "height": 13.96875,
                  "width": 59,
                  "x": 0,
                  "y": 0
                },
                "width": 160,
                "x": 1,
                "y": -30.000149
              }
            ],
            "height": 41.96875,
            "id": "n1",
            "label": {
              "content": "emp",
              "fontFamily": "Segoe UI Symbol",
              "fontSize": "12",
              "height": 17.96875,
              "width": 162,
              "x": 0,
              "y": 0
            },
            "width": 162,
            "x": 0,
            "y": -51.9689
          }
        ],
        "edges": [
          {
            "id": "e0",
            "sourceId": "n1::n0",
            "targetId": "n0::n0"
          }
        ]
      },
      "tooltip": {},
      "listIdMap": {
        "n0": [
          "12"
        ],
        "n0::n0": [
          "13"
        ],
        "n1": [
          "4"
        ],
        "n1::n0": [
          "17"
        ]
      }
    }
  },
  "error": "find orphan column(10500) near: ename(1,8)\r\nLink orphan column [ename] to the first table [emp]",
  "sessionId": "1491a5d5071c220ab993aa4d8a2e0e477d83abe4dd976a0c5c56c69e886a9481_1667231780609"
}
```
