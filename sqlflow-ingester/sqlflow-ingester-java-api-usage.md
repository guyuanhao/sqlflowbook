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
//数据库主机（ip地址或域名）
source.setHostname("localhost");
//端口
source.setPort("3306");
//数据库名称
source.setDatabase("test");
//数据库登录用户名
source.setAccount("root");
//数据库登录密码
source.setPassword("123456");
//数据库类型，详见：支持的dbVendor列表,第二个参数是数据库版本，可以为空。 
DbVendor dbVendor = new DbVendor("dbvmysql", "5.7");
source.setDbVendor(dbVendor);
//执行导出元数据，支持返回对象和json字符串两种形式
SqlflowExporter exec = new SqlflowExporter();
//返回对象
Result<SQLFlow> result1 = exec.exporterMetadata(source);
//返回json字符串
Result<String> result2 = exec.exporterMetadataString(source);
```
