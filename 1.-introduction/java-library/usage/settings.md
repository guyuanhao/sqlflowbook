# Settings

Simple mode is enabled when `/s` flag is added to the command:

```bash
java -jar gudusoft.dlineage.jar /t mssql /f path_to_sql_file /s
```

simple mode 最主要的特点就是忽略中间结果集，缺省情况下，只显示fdd关系。

simple mode的显示结果受option的影响，option包含两个选项 setSimpleShowTopSelectResultSet，setSimpleShowFunction

setSimpleShowTopSelectResultSet：是否显示top select resulset，默认false

setSimpleShowFunction：是否显示function, 默认 false

既缺省情况下，是不会显示top select resultset和function的，但是可以通过选项来控制，而sqlflow因为UI显示的原因，setSimpleShowTopSelectResultSet是强制为true的，一定会显示顶级select语句的结果集。

另外 dataflowAnalyzer 提供了一个方法 dataflow getSimpleDataflow(dataflow instance, boolean simpleOutput, List `<String>` types)，可以对非simple模式的dataflow进行处理，并且可以指定处理的关系类型，该方法可以处理fdr关系，既同时也对fdr关系进行追踪，而不仅仅是fdd关系。

dataflow getSimpleDataflow(dataflow instance, boolean simpleOutput, List `<String>` types)

参数：

* dataflow：非simple模式的dataflow
* simpleOutput
  * false showTopSelectResultSet为true
  * true showTopSelectResultSet为false
* types：关系类型列表，可以为fdd, fdr，当包含fdr时，也会对fdr关系进行追踪

In Simple mode, the intermediate results will not be displayed&#x20;
