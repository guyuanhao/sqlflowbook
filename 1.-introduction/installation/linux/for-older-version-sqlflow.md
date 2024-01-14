# For older version SQLFlow under Linux

## <mark style="color:red;">**This page is for SQLFlow 5.x.x.x**</mark>

Please refer to the latest install manual if you are using the latest SQFlow(version > 6.0.0.0):

{% content-ref url="../linux.md" %}
[linux.md](../linux.md)
{% endcontent-ref %}

You can check this page for the SQLFlow berfore version&#x20;

{% content-ref url="../versions/sqlflow-before-version-6.md" %}
[sqlflow-before-version-6.md](../versions/sqlflow-before-version-6.md)
{% endcontent-ref %}

***

{% embed url="https://www.youtube.com/watch?t=23s&v=dZsNRWHAPo4" %}
Installation Guide - Linux
{% endembed %}

### Prerequisites

* [SQLFlow on-premise version](https://www.gudusoft.com/sqlflow-on-premise-version/)
* A linux server with at least 8GB memory (ubuntu 20.04 is recommended).
* Java 8
* Nginx web server.
* Port needs to be opened. (80, 8761,8081,8083. Only 80 port need to be opened if you setup the nginx reverse proxy as mentioned in the below)

### Setup Environment (Ubuntu for example)

```
sudo apt-get update
sudo apt-get install nginx -y
sudo apt-get install default-jre -y	
```

CentOS

* [How To Install Nginx on CentOS](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-centos-7)
* [How To Install Java on CentOS](https://www.digitalocean.com/community/tutorials/how-to-install-java-on-centos-and-fedora)

### Upload Files

create a directory :

```bash
# it must be created start with root path
sudo mkdir -p /wings/sqlflow
```

upload your zip file including backend and frontend file to `sqlflow` folder, and unzip like this :

```bash
unzip sqlflow.zip
```

You should get files organized like this:

```
/wings/
└── sqlflow
    ├── backend
    │   ├── bin
    │   │   ├── backend.bat 
    │   │   ├── backend.sh
    │   │   ├── eureka.bat
    │   │   ├── eureka.sh
    │   │   ├── eureka.vbs
    │   │   ├── gspLive.bat
    │   │   ├── gspLive.sh  
    │   │   ├── gspLive.vbs  
    │   │   ├── monitor.bat
    │   │   ├── monitor.sh 
    │   │   ├── sqlservice.bat
    │   │   ├── sqlservice.sh 
    │   │   ├── sqlservice.vbs
    │   │   ├── stop.bat
    │   │   ├── stop.sh
    │   ├── lib
    │   │   ├── eureka.jar
    │   │   ├── gspLive.jar  
    │   │   ├── sqlservice.jar
    │   ├── conf
    │   │   ├── gudu_sqlflow_license.txt     
    │   │   ├── gudu_sqlflow.conf     
    │   ├── data
    │   │   ├── job  
    │   │   │   ├── task     
    │   │   │   ├── {userid}   
    │   │   ├── schema     
    │   │   ├── session     
    │   │   ├── version     
    │   ├── log
    │   ├── tmp
    │   │   └── cache  
    └── frontend
        ├── config.public.json
        ├── images
        │   ├── check.svg
        │   ├── Join.svg
        │   ├── pic_Not logged in.png
        │   └── visualize.svg
        ├── index.********************.css
        ├── index.********************.css
        ├── index.********************.css
        ├── index.********************.css
        └── index.html
        └── lang
        ├── page.*********************.js
        ├── page.*********************.js
        ├── page.*********************.js
        ├── page.*********************.js
        ├── public.*********************.js
        ├── widget
        │   ├── index.js
        │   ├── sqlflow-library.version.css
        │   └── sqlflow-library.version.js
```

set folder permissions :

```bash
sudo chmod -R 755 /wings/sqlflow
```

### Nginx Reverse Proxy

**1. Config Nginx**

open your nginx configuration file ( at `/etc/nginx/sites-available/default` under ubuntu ), add a server :

```nginx
server {
	listen 80 default_server;
	listen [::]:80 default_server;

	root /wings/sqlflow/frontend/;
	index index.html;

	location ~* ^/index.html {
		add_header X-Frame-Options deny; # remove this line if you want embed sqlflow in iframe
		add_header Cache-Control no-store;
	}

	location / {
		try_files $uri $uri/ =404;
	}
	
	location /api/ {
		proxy_pass http://127.0.0.1:8081/;
		proxy_connect_timeout 600s ;
		proxy_read_timeout 600s;
		proxy_send_timeout 600s;
		
		proxy_set_header Host $host;
		proxy_set_header X-Real-IP $remote_addr;
		proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
		proxy_set_header User-Agent $http_user_agent;  
	}
}
```

note that `8081` in `proxy_pass http://127.0.0.1:8081/` should be consistent to gspLive.jar's port.

`/api` is mapped to `http://127.0.0.1:8081` in the above configration. This is useful if you company doesn't allow access `8081` port from the external.

**2. modify frontend configuration file config.private.json**

* Open the configration file "/wings/sqlflow/frontend/config.private.json"
* Modify the **ApiPrefix** attribute

```
  "ApiPrefix": "/api"
```

### Customize the port

If you don't want to change the default service port you can just ignore this section. Otherwise this section will show you how to customize the port.

#### 1. Default port

1. Web port is `80`
2. SQLFlow backend service port:

| File           | Port |
| -------------- | ---- |
| eureka.jar     | 8761 |
| gspLive.jar    | 8081 |
| sqlservice.jar | 8083 |

#### 2. Modify the web port

Change the default web port from `80` to `9000` (or any port you like).

<figure><img src="../../../.gitbook/assets/sqlflow-install-customize-web-port.png" alt=""><figcaption></figcaption></figure>

#### 3. Modify java service port

Change the default gspLive port from `8081` to `9001`(or any port you like).&#x20;

**Step 1: Change the port in nginx config file**

<figure><img src="../../../.gitbook/assets/sqlflow-install-customize-gsplive-port-nginx.png" alt=""><figcaption></figcaption></figure>

**Step 2: Change the port in gspLive.sh(gspLive.bat)**&#x20;

<figure><img src="../../../.gitbook/assets/sqlflow-install-customize-port-gsplive.png" alt=""><figcaption></figcaption></figure>



### Start Backend Services

start service in background:

```bash
sudo /wings/sqlflow/backend/bin/backend.sh
```

please allow 3-5 minutes to start the service.

use `ps -ef|grep java` to check those 3 processing are running.

```
ubuntu   11047     1  0 Nov02 ?        00:04:44 java -server -jar eureka.jar
ubuntu   11076     1  0 Nov02 ?        00:04:11 java -server -Xmn512m -Xms2g -Xmx2g -Djavax.accessibility.assistive_technologies=  -jar sqlservice.jar
ubuntu   11114     1  0 Nov02 ?        00:05:17 java -server -jar gspLive.jar
```

### Start Frontend Services

start your nginx :

```bash
sudo service nginx start
```

or reload :

```bash
sudo nginx -s reload
```

open http://yourdomain.com/ to see the SQLFlow.

open http://yourdomain.com/api/gspLive\_backend/doc.html?lang=en to see the Restful API documention. OR

open http://yourdomain.com:8081/gspLive\_backend/doc.html?lang=en to see the Restful API documention.

### Gudu SQLFlow License file

If this is the first time you setup the Gudu SQLFlow on a new machine, then, you will see this license UI:&#x20;

<figure><img src="../../../.gitbook/assets/gudu-sqlflow-license.png" alt=""><figcaption></figcaption></figure>

1. You send us the Gudu SQLFlow Id (6 characters in red).
2. We will generate a license file for you based on this id.
3. You upload the license file by click the "upload license file" link.

### Backend Services Configuration

sqlflow provides several optioins to control the service analysis logic. Open the sqlservice configuration file(conf/gudu\_sqlflow.conf)

* **relation\_limit**: default value is 1000. When the count of selected object relations is greater than relation\_limit, sqlflow will fallback to the simple mode, ignore all the record sets. If the relations of simple mode are still greater than relation\_limit, sqlflow will only show the summary information.
* **big\_sql\_size**: default value is 4096. If the sql length is greater than big\_sql\_size, sqlflow submit the sql in the work queue and execute it. If the work queue is full, sqlflow throws an exception and return error message "Sorry, the service is busy. Please try again later."

### Sqlflow client api call

See [sqlflow client api call](https://github.com/sqlparser/sqlflow\_public/blob/master/api/sqlflow\_api\_full.md#webapi)

1. Get userId from gudu\_sqlflow.conf

* Open the configration file "/wings/sqlflow/backend/conf/gudu\_sqlflow.conf"
* The value of anonymous\_user\_id field is webapi userId

```bash
  anonymous_user_id=xxx
```

* **Note:** on-promise mode, webapi call doesn't need the token parameter

1.  Test webapi by curl

    * test sql:

    ```sql
      select name from user
    ```

    * curl command:

    ```bash
      curl -X POST "http://yourdomain.com/api/gspLive_backend/sqlflow/generation/sqlflow" -H "accept:application/json;charset=utf-8" -F "userId=YOUR USER ID HERE" -F  "dbvendor=dbvoracle" -F "sqltext=select name from user"
    ```

    * response:

    ```json
      {
        "code": 200,
        "data": {
          "dbvendor": "dbvoracle",
          "dbobjs": [
            ...
          ],
          "relations": [
            ...
          ]
        },
        "sessionId": ...
      }
    ```

    * If the code returns **401**, please check the userId is set or the userId is valid.

### Enable Regular Job

If you need to enable regular job feature on your sqlflow on-premiser, you will also need to install Clickhouse on your server. Check here for Clickhouse installation:

{% content-ref url="../clickhouse-installation/" %}
[clickhouse-installation](../clickhouse-installation/)
{% endcontent-ref %}
