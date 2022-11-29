# Analyze data linege from a database

The dlineage tool can connect to the database instance and analyze the metadata to generate the data lineage automatically.

## Connect and analyze data lineage

Use `/fromdb` parameter to export metadta from the database.

`/fromdb` parameter:

\-dbVendor: Database type, Use colon to split dbVendor and version if specific version is required. (:, such as dbvmysql:5.7)

\-host: Database host name (ip address or domain name)

\-port: Port number

\-db: Database name

\-user: User name

\-pwd: User password

\-extractedDbsSchemas: Export metadata under the specific schema. Use comma to split if multiple schema required. We can use this flag to improve the export performance.

\-excludedDbsSchemas: Exclude metadata under the specific schema during the export. Use comma to split if multiple schema required (such as ,). We can use this flag to improve the export performance.

\-extractedViews: Export metadata under the specific view. Use comma to split if multiple views required (such as ,). We can use this flag to improve the export performance.

`/exportonly` just export metadata.json, no further data analysis.

`/metadataoutput` specifies the metadata output directory and file name.

for example, connect to an Oracle database and analzye the data lineage.

```
java -jar data_flow_analyzer.jar /fromdb "-dbVendor dbvoracle -host 127.0.0.1 -port 1521 -db orcl -user scott -pwd tiger"
```

## Export the meatadata only

You can also export the meatadata from database and analzye the metadata in two steps:

* Only export the metadta

```
java -jar data_flow_analyzer.jar /fromdb "-dbVendor dbvoracle -host 127.0.0.1 -port 1521 -db orcl -user scott -pwd tiger" /exportonly  /metadataoutput metadata.json
```

the metadata.json exported in this step can also be used with `/env` paramter to resolve the ambiguous columns problem in SQL query.

* analyze the metadta that generated in the previous step

```
java -jar gudusoft.dlineage.jar /t oracle /f metadata.json
```
