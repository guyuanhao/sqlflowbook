---
description: https://e.gitee.com/gudusoft/docs/1006527/file/2767137?sub_id=5768619
---

# SQLFlow-Ingester Java API Usage

This page gives a Java code example to embed the SQLFlow-Ingester in your Java programme.

```java
//1.import the following Ingester library 
import com.gudu.sqlflow.ingester.exporter.SqlflowExporter;
import com.gudu.sqlflow.ingester.library.domain.DataSource;
import com.gudu.sqlflow.ingester.library.domain.DbVendor;
import com.gudu.sqlflow.ingester.library.domain.sqlflow.SQLFlow;
import com.gudu.sqlflow.ingester.library.result.Result;

//2.Give the database parameters before invoking the Ingester
DataSource source = new DataSource();
//database host name (ip address or domain name) 
source.setHostname("localhost");
//port
source.setPort("3306");
//database name
source.setDatabase("test");
//user namer
source.setAccount("root");
//database password
source.setPassword("123456");
//Database type and version number, Check "List of Supported dbVerdors" section for a full list of the supported databases.
//The second parameter can be null if no specific version need to be provided
DbVendor dbVendor = new DbVendor("dbvmysql", "5.7");
source.setDbVendor(dbVendor);
//Export the metadata, the result can be in object/json string.
SqlflowExporter exec = new SqlflowExporter();
//Take the result in SQLFLow object
Result<SQLFlow> result1 = exec.exporterMetadata(source);
//Take the result in json string
Result<String> result2 = exec.exporterMetadataString(source);
```
