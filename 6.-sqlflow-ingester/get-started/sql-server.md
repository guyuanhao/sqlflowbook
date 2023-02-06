---
description: https://e.gitee.com/gudusoft/docs/1006527/file/2767137?sub_id=7687947
---

# SQL Server

Please ensure you have the prerequisites and the package listed in [this page](../introduction/sqlflow-submitter.md#prerequisites) before start creating the [SQLFlow Job](../../1.-introduction/getting-started/different-modes-in-gudu-sqlflow/job-mode.md) and connecting SQLFlow server.

This page provides detailed conguration steps to submit Job for **SQL Server**.

## Command

### Windows&#x20;

```
submitter.bat -f <path_to_config_file>  
e.g.
    submitter.bat -f D:/mssql-winuser-config.json
```

### Linux & Mac

```bash
bash submitter.sh -f <path_to_config_file>  

note: 
    path_to_config_file: the full path to the config file

e.g.
    bash submitter.sh -f /home/workspace/gudu_ingester/submitter_config.json
```

## SQL Server Sample Config File

```json
{
	"databaseServer":{
		"hostname":"DESKTOP-MLUR76N\\SQLEXPRESS",
		"port":"1443",
		"database":"master",
		"extractedDbsSchemas":"",
	        "excludedDbsSchemas":"",
	        "extractedStoredProcedures":"",
	        "extractedViews":"",
		"enableQueryHistory":false,
		"queryHistoryBlockOfTimeInMinutes":0,
		"sqlsourceTableName":"",
		"sqlsourceColumnQuerySource":"",
		"sqlsourceColumnQueryName":"",
		"authentication":"windowsuser"
	},
	"sqlFlowServer":{
		"server":"http://sqlflow.cn",
		"serverPort":"8081",
		"userId":"gudu|0123456789",
		"userSecret":"xxx"
	},
	"sqlScriptSource":"database",
	"lineageReturnFormat":"json",
	"lineageReturnOutputFile":"",
	"databaseType":"mssql",
	"taskName": "sumitterTest",
	"jobNameToId": 1,
	"jobType":"regular"
}

```

For the detailed field description, please refer to [this page](../introduction/sqlflow-submitter.md#configuration-fields).
