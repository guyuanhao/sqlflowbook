---
description: >-
  https://github.com/sqlparser/sqlflow_public/tree/master/grabit#what-is-a-grabit
---

# SQLFlow-Submitter

With SQLFlow-Submitter, you will be able to submit SQL and metadata to the SQLFlow server, to create jobs, to generate data lineage as well as to have the results in the UI.

## Prerequisites

*   SQLFlow-Ingester package

    Download our latest SQFlow-Ingester package [here](https://github.com/sqlparser/sqlflow\_public/releases).
* Java 8 or higher version must be installed and configured correctly.

## Install

```
unzip sqlflow-ingesterx.x.x.zip -d <ingester_folder>

cd <ingester_folder>
```

* **Linux & mac open permissions**

```
chmod 777 *.sh
```

## Usage

<figure><img src="../../.gitbook/assets/图片.png" alt=""><figcaption></figcaption></figure>

After decompressing the package, you will find `submitter.bat` for Windows and `submitter.sh` for Linux & Mac.&#x20;

* Windows&#x20;

```
submitter.bat -f D:/mssql-winuser-config.json
```

* Linux & Mac

```bash
bash submitter.sh -f <path_to_config_file>  

note: 
    path_to_config_file: the full path to the config file

eg: 
    bash submitter.sh -f /home/workspace/gudu_ingester/submitter_config.json
```

If you are on Linux or Mac, you can schedule the submitter with `crontab` to create a cron job.

```
crontab -e
```

In the editor, let's say now we want schedule a daily cron job add the following code

```bash
0 0 * * * bash submitter.sh -f <path_to_config_file> <lib_path>

note: 
    path_to_config_file: config file path 
    lib_path: lib directory absolute path
```

Please check [this document](https://phoenixnap.com/kb/set-up-cron-job-linux) for more information about cron.

## SQLFlow-Submitter Log

The logs of the submitter are persisted under `log` folder.

<figure><img src="../../.gitbook/assets/微信图片_20230202230033.png" alt=""><figcaption></figcaption></figure>

### **Common Log Description**

* file is not a valid file.

The file does not exist or the file address cannot be found.

* sqlScriptSource is valid, support source are database,gitserver,singleFile,directory

The `sqlScriptSource` parameter is incorrectly set. Data sources are only supported from databases, remote repositories, and files and directories

* lineageReturnFormat is valid, support types are json,csv,graphml

Parameter `lineageReturnFormat` is incorrectly set. The data lineage result obtained can only be in JSON, CSV, and GraphML formats

* export metadata in json successful. the resulting metadata is as follows

Exporting metadata from the specified database succeeded.

* This database is not currently supported

Parameter `databaseType` set error, at present only support access, bigquery, couchbase, dax, db2, greenplum, hana, hive, impala, informix, mdx, mssql,sqlserver,mysql,netezza,odbc,openedge,oracle,postgresql,postgres,redshift,snowflake,sybase,teradata,soql,vertica,azure

* db connect failed

The metadata fails to be exported from the specified database. If the metadata fails to be exported, check whether the database connection information in the `dataServer` object is correct

* export metadata in json failed

Failed to export metadata from the specified database. Check whether the user who logs in to the database has the permission to obtain metadata

* metadata is empty

Exporting metadata from specified database is empty, please contact me for processing

* remote warehouse url cannot be empty

The URL in the gitServer parameter cannot be empty

* remote warehouse pull failed

Failed to connect to the remote warehouse. Check whether the remote warehouse connection information is correct

* connection failed，repourl is the ssh URL

The remote repository address is incorrect. Please check whether it is a Git address

* remote warehouse file to zip successful. path is：xx

Pull to a local storage address from a remote repository

* get token from sqlflow failed

Failed to connect to SQLFlow. Check whether connection parameters of `sqlflowServer` are correct

* submit job to sqlflow failed, please input https with url

Failed to submit the SQLFlow task. Check whether the URL and port of the `sqlflowServer` are correct

* submit job to sqlflow failed

Failed to submit the SQLFLOW task. Check whether the sqlFLOW background service is started properly

* get job to status failed

After a job is submitted to SQLFLOW, SQLFlow fails to execute the job

* export json result failed

Description Failed to export Data Lineage in JSON format from SQLflow

* export csv result failed

Description Failed to export Data Lineage in csv format from SQLflow

* export diagram result failed

Description Failed to export Data Lineage in diagram format from SQLflow

* submit job to sqlflow successful

The job is successfully submitted to SQLFlow, and the basic information about the submitted job is displayed

* \[database: 0 table: 0 view: 0 procedure: 0 column: 0 synonym: 0]

Statistics the amount of metadata exported from the specified database

* the time taken to export : 0ms

Time, in milliseconds, to export metadata from the specified database

* download success, path: xxx

Local storage address of Data Lineage returned after successfully submitting a job to SQLFlow

* job id is : xxxx

job id from sqlflow , log in to the SQLFlow website to view the newly analyzed results. In the `Job List`, you can view the analysis results of the currently submitted tasks.

* The number of relationships in this task is too large to export this file, please check blood relationships on SQLFlow platform.

When the task uploaded to SQLFlow is too large or the number of rolls parsed by SQLFlow is too large, SQLFlow-Submitter cannot obtain CSV files from it.
