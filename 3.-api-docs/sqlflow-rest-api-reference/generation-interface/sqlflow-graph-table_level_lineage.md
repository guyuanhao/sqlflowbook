# /sqlflow/graph/table\_level\_lineage

{% swagger src="../../../.gitbook/assets/swagger.yaml" path="/sqlflow/generation/sqlflow/graph/table_level_lineage" method="post" %}
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
      "mostRelationTables": [],
      "column": 4,
      "relationship": 0,
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
        }
      ],
      "relationships": [],
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
      "relationshipIdMap": {},
      "elements": {
        "tables": [],
        "edges": []
      },
      "tooltip": {},
      "listIdMap": {}
    }
  },
  "sessionId": "1491a5d5071c220ab993aa4d8a2e0e477d83abe4dd976a0c5c56c69e886a9481_1667481872808"
}
```
