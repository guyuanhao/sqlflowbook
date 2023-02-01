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
