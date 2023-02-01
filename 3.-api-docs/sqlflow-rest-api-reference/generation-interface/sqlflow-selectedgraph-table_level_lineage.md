# /sqlflow/selectedgraph/table\_level\_lineage

{% swagger src="../../../.gitbook/assets/swagger.yaml" path="/sqlflow/generation/sqlflow/selectedgraph/table_level_lineage" method="post" %}
[swagger.yaml](../../../.gitbook/assets/swagger.yaml)
{% endswagger %}

Sample response:

```json
{
  "code": 200,
  "data": {
    "mode": "global",
    "summary": {
      "schema": 0,
      "process": 1,
      "database": 0,
      "view": 0,
      "mostRelationTables": [
        {
          "table": "TBL_TEMP1"
        },
        {
          "table": "TBL_TEMP2"
        }
      ],
      "column": 0,
      "relationship": 2,
      "table": 2
    },
    "sqlflow": {
      "dbvendor": "dbvoracle",
      "dbobjs": [
        {
          "id": "6",
          "name": "QUERY INSERT-1",
          "type": "process",
          "coordinates": [
            {
              "x": 1,
              "y": 1,
              "hashCode": "0"
            },
            {
              "x": 1,
              "y": 112,
              "hashCode": "0"
            }
          ],
          "queryHashId": "4cc55e0b4d63c3e07927d59f117c8851"
        },
        {
          "id": "4",
          "name": "TBL_TEMP2",
          "type": "table",
          "columns": [],
          "coordinates": [
            {
              "x": 1,
              "y": 13,
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
          "id": "10",
          "name": "TBL_TEMP1",
          "type": "table",
          "columns": [],
          "coordinates": [
            {
              "x": 1,
              "y": 67,
              "hashCode": "0"
            },
            {
              "x": 1,
              "y": 76,
              "hashCode": "0"
            }
          ]
        }
      ],
      "relationships": [
        {
          "id": "504",
          "type": "fdd",
          "target": {
            "id": "6",
            "coordinates": []
          },
          "sources": [
            {
              "id": "10",
              "sourceId": "10",
              "sourceName": "TBL_TEMP1",
              "coordinates": []
            }
          ]
        },
        {
          "id": "506",
          "type": "fdd",
          "target": {
            "id": "4",
            "coordinates": []
          },
          "sources": [
            {
              "id": "6",
              "sourceId": "6",
              "sourceName": "QUERY INSERT-1",
              "coordinates": []
            }
          ]
        }
      ]
    },
    "graph": {
      "relationshipIdMap": {
        "e0": [
          "506",
          "fdd"
        ],
        "e1": [
          "504",
          "fdd"
        ]
      },
      "elements": {
        "tables": [
          {
            "columns": [],
            "height": 25.96875,
            "id": "n0",
            "label": {
              "content": "Query Insert-1",
              "fontFamily": "Segoe UI Symbol",
              "fontSize": "12",
              "height": 17.96875,
              "width": 162,
              "x": 0,
              "y": 0
            },
            "width": 162,
            "x": 212,
            "y": -35.9689
          },
          {
            "columns": [],
            "height": 25.96875,
            "id": "n1",
            "label": {
              "content": "tbl_temp2",
              "fontFamily": "Segoe UI Symbol",
              "fontSize": "12",
              "height": 17.96875,
              "width": 162,
              "x": 0,
              "y": 0
            },
            "width": 162,
            "x": 424,
            "y": -35.9689
          },
          {
            "columns": [],
            "height": 25.96875,
            "id": "n2",
            "label": {
              "content": "tbl_temp1",
              "fontFamily": "Segoe UI Symbol",
              "fontSize": "12",
              "height": 17.96875,
              "width": 162,
              "x": 0,
              "y": 0
            },
            "width": 162,
            "x": 0,
            "y": -35.9689
          }
        ],
        "edges": [
          {
            "id": "e0",
            "sourceId": "n0",
            "targetId": "n1"
          },
          {
            "id": "e1",
            "sourceId": "n2",
            "targetId": "n0"
          }
        ]
      },
      "tooltip": {},
      "listIdMap": {
        "n0": [
          "6"
        ],
        "n1": [
          "4"
        ],
        "n2": [
          "10"
        ]
      }
    }
  },
  "sessionId": "98f82119a46175bb8e4ed971133f2953ea66556107e438030df2a3217bb67baa_1666495937504"
}
```
