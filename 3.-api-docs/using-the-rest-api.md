# Using the Rest API

In this article, we will be using `Curl` to demonstrate the usage of the Rest API. You can use any preferred programming language or any tools as you like.

You may also want to directly interact with our online API using [Swagger UI](swagger-ui.md).

### **1. Generate a token**

Once you have the `userid` and `secret key` (please check [this page](prerequisites.md#generate-account-secret) for how to get the `userid` and `secret key`), the first API need to be called is:

```
/gspLive_backend/user/generateToken
```

This API will return a temporary token that needs to be used in the API call thereafter.

```
curl -X POST "https://api.gudusoft.com/gspLive_backend/user/generateToken" -H  "Request-Origion:testClientDemo" -H  "accept:application/json;charset=utf-8" -H  "Content-Type:application/x-www-form-urlencoded;charset=UTF-8" -d "secretKey=YOUR SECRET KEY" -d "userId=YOUR USER ID HERE"
```

**Tips**: If you are using SQLFLow On-Premise,  **token might not be required** if you have set following flag in `/wings/sqlflow/backend/conf/gudu_sqlflow.conf`

```bash
ignore_user_token=true
```

### **2. Generate the data lineage**

Call this API by sending the SQL query and get the result includes the data lineage.

```
/gspLive_backend/sqlflow/generation/sqlflow
```

**SQLFlow Cloud Server**

```
curl -X POST "https://api.gudusoft.com/gspLive_backend/sqlflow/generation/sqlflow?showRelationType=fdd" -H  "Request-Origion:testClientDemo" -H  "accept:application/json;charset=utf-8" -H  "Content-Type:multipart/form-data" -F "sqlfile=" -F "dbvendor=dbvoracle" -F "ignoreRecordSet=false" -F "simpleOutput=false" -F "sqltext=CREATE VIEW vsal  as select * from emp" -F "userId=YOUR USER ID HERE"  -F "token=YOUR TOKEN HERE"
```

### **3. Export the data lineage in csv format**

Call this API by sending the SQL file and get the csv result includes the data lineage.

```
/gspLive_backend/sqlflow/generation/sqlflow/exportFullLineageAsCsv
```

```
curl -X POST "https://api.gudusoft.com/gspLive_backend/sqlflow/generation/sqlflow/exportFullLineageAsCsv" -H  "accept:application/json;charset=utf-8" -H  "Content-Type:multipart/form-data" -F "userId=YOUR USER ID HERE" -F "token=YOUR TOKEN HERE" -F "dbvendor=dbvoracle" -F "sqlfile=@YOUR UPLOAD FILE PATH HERE" --output YOUR DOWNLOAD FILE PATH HERE
```

Sample:

```
curl -X POST "https://api.gudusoft.com/gspLive_backend/sqlflow/generation/sqlflow/exportLineageAsCsv" -H  "accept:application/json;charset=utf-8" -H  "Content-Type:multipart/form-data" -F "userId=auth0|5fc8e95991a780006f180d4d" -F "token=YOUR TOKEN HERE" -F "dbvendor=dbvoracle" -F "sqlfile=@c:\prg\tmp\demo.sql" --output c:\prg\tmp\demo.csv
```

**Note:**

* \-H "Content-Type:multipart/form-data" is required.
* Add **@** before the upload file path
* \--output is required.
* Optional, if you just want to fetch table to table relations, please add **-F "tableToTable=true"**

### **4. Submit multiple SQL files and get the data lineage in CSV, JSON, graphml format.**

The following Apis can take multiple SQL files as the input of analysis. Compress your SQL files into one **zip file** and upload the archive zip file as request body if you wish to submit multiple SQL files.

{% content-ref url="sqlflow-rest-api-reference/generation-interface/sqlflow-generation-sqlflow-exportlineageascsv.md" %}
[sqlflow-generation-sqlflow-exportlineageascsv.md](sqlflow-rest-api-reference/generation-interface/sqlflow-generation-sqlflow-exportlineageascsv.md)
{% endcontent-ref %}

{% content-ref url="sqlflow-rest-api-reference/job-interface/" %}
[job-interface](sqlflow-rest-api-reference/job-interface/)
{% endcontent-ref %}

### The full reference to the Rest APIs

{% content-ref url="sqlflow-rest-api-reference/" %}
[sqlflow-rest-api-reference](sqlflow-rest-api-reference/)
{% endcontent-ref %}

### Troubleshooting

* Under windows, you may need to add option `--ssl-no-revoke` to avoid some security issues, `curl --ssl-no-revoke`
