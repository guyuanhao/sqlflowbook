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
username: sqlflowadmin@gudusoft.com
password: Tool4Datalineage@gudusoft

Basic Account
username: sqlflowuser@gudusoft.com
password: MyDatalineage@123 
```

<figure><img src="../../.gitbook/assets/图片 (13).png" alt=""><figcaption></figcaption></figure>

## The Docker Image

Pull the sqlflow docker image:

```bash
docker pull gudusqlflow/sqlflow-simple-trial:5.7.3
```

## Create the SQLFlow Container

```bash
docker run -it -p7090:80 --name mysqlflow gudusqlflow/sqlflow-simple-trial:5.7.3
```

The `7090` in the above command will be the port to visit SQLFlow UI. You can change the port if 7090 is occupied in your machine.&#x20;

The `mysqlflow` is the name of the container. For more information of the container creation, you can check [the official Docker Doc](https://docs.docker.com/engine/reference/commandline/container/).

<figure><img src="../../.gitbook/assets/图片 (14).png" alt=""><figcaption></figcaption></figure>

Use http://\<your ip>:\<port> to reach sqlflow UI.

## Troubleshooting

The following issue only occurs in Centos stream9, we don't foresee the error in Centos 7, Centos stream8, Ubuntu20 or Debian11.

### 1. Get License fail

<figure><img src="../../.gitbook/assets/图片 (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

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

<figure><img src="../../.gitbook/assets/图片 (5).png" alt=""><figcaption></figcaption></figure>

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
