# Upgrade

This page shows you how to upgrade from SQLFlow 5.x to SQLFlow 6.x

You can refer to the following page if you would like to know the difference between SQLFlow 5.x and SQLFlow 6.x

{% content-ref url="../../8.-other/change-logs.md" %}
[change-logs.md](../../8.-other/change-logs.md)
{% endcontent-ref %}

### Step1: Backup Old Data

```bash
mv /wings/sqlflow/* /wings/bak/sqlflow
```

### Step2: Install the SQLFlow 6.x

{% content-ref url="./" %}
[.](./)
{% endcontent-ref %}

### Step3: Migrate your SQLFlow Jobs

```bash
cp -r <old sqlflow backup>/data/job/*  <new sqlflow>/data/job/
```

### Step4: Migrate your SQLFlow Data

```bash
cp -r <old sqlflow backup>/conf/sqlflow.sqlite  <new sqlflow>/conf/
```

### Step5: Move your License File

```bash
cp -r <old sqlflow backup>/conf/gudu_sqlflow_license.txt  <new sqlflow>/conf/
```

### Step6: Start SQLFlow 6.x

```bash
sudo /wings/sqlflow/backend/bin/backend.sh
```

Please send an email to support@gudusoft.com if there's any issues with your license file.
