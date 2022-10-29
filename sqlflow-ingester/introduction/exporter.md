# Exporter

SQLFlow-exporter is the main functionality of the SQLFlow-Ingester. It is used to getting the metadata from different databases.

### SQLFlow-Exporter Usage

Under linux:

```
./exporter.sh -host 127.0.0.1 -port 1521 -db orcl -user scott -pwd tiger -save /tmp/sqlflow-ingester -dbVendor dbvoracle
```

Under windows:

```
exporter.bat -host 127.0.0.1 -port 1521 -db orcl -user scott -pwd tiger -save c:\tmp\sqlflow-ingester -dbVendor dbvoracle
```

Or you can directly execute the .jar package, the jar packages are under the `./lib` folder:&#x20;

```
java -jar sqlflow-exporter-1.0.jar  -host 106.54.134.160 -port 1521 -db orcl -user bigking -pwd Cat_12345 -save d:/ -dbVendor dbvoracle
```

A metadata.json file will be generated after successfully export metadta from the database.&#x20;

Example for the success output:&#x20;

```
exporter metadata success: <-save>/metadata.json
```

Check [here](../list-of-supported-dbvendors.md) for a full list of the supported databases.
