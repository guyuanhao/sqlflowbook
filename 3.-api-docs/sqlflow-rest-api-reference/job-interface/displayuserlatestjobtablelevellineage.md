# /displayUserLatestJobTableLevelLineage

{% swagger src="../../../.gitbook/assets/swagger_without_token.yaml" path="/sqlflow/job/displayUserLatestJobTableLevelLineage" method="post" %}
[swagger_without_token.yaml](../../../.gitbook/assets/swagger_without_token.yaml)
{% endswagger %}

Sample response:

```json
{
  "jobId": "939fdbbaf52b45139b86c0761d6036b0",
  "code": 200,
  "data": {
    "mode": "global",
    "summary": {
      "schema": 0,
      "process": 1,
      "database": 0,
      "view": 0,
      "mostRelationTables": [],
      "column": 3,
      "relationship": 0,
      "table": 1
    },
    "sqlflow": {
      "dbvendor": "dbvoracle",
      "relationships": [],
      "dbobjs": [
        {
          "queryHashId": "04ebc5aec1a07e1db80b0bc798742875",
          "name": "QUERY INSERT-1",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 1,
              "y": 1
            },
            {
              "hashCode": "0",
              "x": 1,
              "y": 73
            }
          ],
          "id": "8",
          "type": "process"
        },
        {
          "columns": [
            {
              "name": "ID",
              "coordinates": [
                {
                  "hashCode": "0",
                  "x": 1,
                  "y": 28
                },
                {
                  "hashCode": "0",
                  "x": 1,
                  "y": 30
                }
              ],
              "id": "5"
            },
            {
              "name": "FIRST_NAME",
              "coordinates": [
                {
                  "hashCode": "0",
                  "x": 1,
                  "y": 32
                },
                {
                  "hashCode": "0",
                  "x": 1,
                  "y": 42
                }
              ],
              "id": "6"
            },
            {
              "name": "LAST_NAME",
              "coordinates": [
                {
                  "hashCode": "0",
                  "x": 1,
                  "y": 44
                },
                {
                  "hashCode": "0",
                  "x": 1,
                  "y": 53
                }
              ],
              "id": "7"
            }
          ],
          "name": "RAW_CUSTOMERS",
          "coordinates": [
            {
              "hashCode": "0",
              "x": 1,
              "y": 13
            },
            {
              "hashCode": "0",
              "x": 1,
              "y": 26
            }
          ],
          "id": "4",
          "type": "table"
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
  "sessionId": "24a4455c71fa35c0393d5747f9c23a9d99f32fa4c130a6b8da8d6a7db8d157ae_1664880305725",
  "job": {
    "ignoreFunction": true,
    "lastExecuteTime": "2022-10-04 10:45:05",
    "schedulable": false,
    "parallel": false,
    "ignoreRecordSet": true,
    "userEmail": "guyuanhao@foxmail.com",
    "persist": false,
    "executeTimeMillis": 0,
    "jobName": "yuanhao1",
    "dataflowOfAggregateFunction": "direct",
    "showTransform": false,
    "sessionId": "24a4455c71fa35c0393d5747f9c23a9d99f32fa4c130a6b8da8d6a7db8d157ae_1664880305725",
    "incremental": false,
    "showConstantTable": false,
    "userId": "auth0|6326be4047c1dfdd3bf553d0",
    "showRelationType": "fdd",
    "subJobs": [],
    "version": "5.2.0",
    "jobId": "939fdbbaf52b45139b86c0761d6036b0",
    "createTime": "2022-10-04 10:45:04",
    "onTop": false,
    "cancelSchedule": false,
    "dbVendor": "dbvoracle",
    "fileNames": [
      "test.sql"
    ],
    "status": "success",
    "executeTime": "0min 1sec"
  }
}
```
