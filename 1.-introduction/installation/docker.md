---
description: https://e.gitee.com/gudusoft/docs/824458/file/1969050?sub_id=5806941
---

# Docker

If you are keen on virtualization and you have [Docker Engine](https://www.docker.com/) installed on your machine, you can also pull SQLFlow's docker image. However, do please note that:

* The SQLFlow docker version is **for testing purposes only**
* After getting the SQLFlow docker version installed, **contact** [**support@gudusoft.com**](mailto:support@gudusoft.com) **with your SQLFlow Id to obtain a 1-month temporary license.**
* The docker version uses the same user management logic as SQLFlow On-Premise. It has the admin account and the basic account.

```
Admin Account
username: admin@local.gudusoft.com
password: admin

Basic Account
username: user@local.gudusoft.com
password: user
```

<figure><img src="../../.gitbook/assets/图片 (13).png" alt=""><figcaption></figcaption></figure>

## The Docker Image

Pull the sqlflow docker image:

```bash
docker pull gudusqlflow/sqlflow-simple-trial:6.1.0.0
```

## Create the SQLFlow Container

```bash
docker run -d -p 7090:8165 --name mysqlflow gudusqlflow/sqlflow-simple-trial:6.1.0.0
```

The `7090` in the above command will be the port to visit SQLFlow UI. You can change the port if 7090 is occupied in your machine.&#x20;

The `mysqlflow` is the name of the container. For more information of the container creation, you can check [the official Docker Doc](https://docs.docker.com/engine/reference/commandline/container/).

<figure><img src="../../.gitbook/assets/图片 (14).png" alt=""><figcaption></figcaption></figure>

Use http://\<your ip>:\<port> to reach sqlflow UI.

## Invoke the SQLFlow API from Docker Container

The SQLFlow API will be available once you have uploaded the license file and get the docker container up running.&#x20;

There's no difference between invoking SQLFlow API from your docker container and from SQLFlow Cloud/On-Premise. Following are some samples to invoke the SQLFlow API from the docker container in Python:

### Generate token

```python
def getToken(userId, server, port, screctKey):
    if userId == 'gudu|0123456789':
        return 'token'
    url = '/api/gspLive_backend/user/generateToken'
    if port != '':
        url = server + ':' + port + url
    else:
        url = server + url
    mapA = {'secretKey': screctKey, 'userId': userId}
    header_dict = {"Content-Type": "application/x-www-form-urlencoded"}

    try:
        r = requests.post(url, data=mapA, headers=header_dict)
    except Exception as e:
        print('get token failed.', e)
    result = json.loads(r.text)

    if result['code'] == '200':
        return result['token']
    else:
        print(result['error'])

```

{% content-ref url="../../3.-api-docs/sqlflow-rest-api-reference/user-interface.md" %}
[user-interface.md](../../3.-api-docs/sqlflow-rest-api-reference/user-interface.md)
{% endcontent-ref %}

### Upload SQL and Retrieve Lineage in CSV

```python
def getResult(userId, token, server, port, delimiter, export_include_table, showConstantTable,
              treatArgumentsInCountFunctionAsDirectDataflow, dbvendor, sqltext, sqlfile):
    url = "/api/gspLive_backend/sqlflow/generation/sqlflow/exportFullLineageAsCsv"
    if port != '':
        url = server + ':' + port + url
    else:
        url = server + url

    files = ''
    if sqlfile != '':
        if os.path.isdir(sqlfile):
            print('The SQL file cannot be a directory.')
            sys.exit(0)
        files = {'sqlfile': open(sqlfile, 'rb')}

    data = {'dbvendor': dbvendor, 'token': token, 'userId': userId}
    if delimiter != '':
        data['delimiter'] = delimiter
    if export_include_table != '':
        data['export_include_table'] = export_include_table
    if showConstantTable != '':
        data['showConstantTable'] = showConstantTable
    if treatArgumentsInCountFunctionAsDirectDataflow != '':
        data['treatArgumentsInCountFunctionAsDirectDataflow'] = treatArgumentsInCountFunctionAsDirectDataflow
    if sqltext != '':
        data['sqltext'] = sqltext
    datastr = json.dumps(data)

    print('start get csv result from sqlflow.')
    try:
        if sqlfile != '':
            response = requests.post(url, data=eval(datastr), files=files)
        else:
            response = requests.post(url, data=eval(datastr))
    except Exception as e:
        print('get csv result from sqlflow failed.', e)
        sys.exit(0)

    print('get csv result from sqlflow successful. result : ')
    print()
    return response.text
```

{% content-ref url="../../3.-api-docs/sqlflow-rest-api-reference/generation-interface/sqlflow-generation-sqlflow-exportlineageascsv.md" %}
[sqlflow-generation-sqlflow-exportlineageascsv.md](../../3.-api-docs/sqlflow-rest-api-reference/generation-interface/sqlflow-generation-sqlflow-exportlineageascsv.md)
{% endcontent-ref %}

Please check our python demo if you need more samples: [https://github.com/sqlparser/sqlflow\_public/blob/master/api/python/basic/getcsv.py](https://github.com/sqlparser/sqlflow\_public/blob/master/api/python/basic/getcsv.py)

## Troubleshooting

The following issue only occurs in Centos stream9, we don't foresee the error in Centos 7, Centos stream8, Ubuntu20 or Debian11.

### 1. Get License fail

<figure><img src="../../.gitbook/assets/图片 (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

If you got this error after launching the docker image, check firstly whether the docker image is running correctly:

```bash
docker ps -a
```

In case of the docker status is `up`, the try to go into the container with:

```bash
docker exec -it mysqlflow /bin/bash
```

Go to the SQLFlow jar folder:

```bash
cd wings/sqlflow/backend/lib
```

Try directly launch the jar file:

```bash
java -jar eureka.jar
```

The error in the following capture means that there is no enough memory for the docker.

<figure><img src="../../.gitbook/assets/图片 (5) (1).png" alt=""><figcaption></figcaption></figure>

You can assign more memory to the docker with:

```bash
mkdir /etc/systemd/system/docker.service.d
sudo vi /etc/systemd/system/docker.service.d/override.conf
```

and then enter

```
[Service]
ExecStart=
ExecStart=/usr/bin/dockerd --default-ulimit nofile=65536:65536 -H fd://
```

Save and run `sudo systemctl daemon-reload` and `sudo systemctl restart docker`.

```shell
sudo systemctl daemon-reload
```

```shell
sudo systemctl restart docker
```
