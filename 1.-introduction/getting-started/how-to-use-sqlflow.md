---
description: https://github.com/sqlparser/sqlflow_public#how-to-use-sqlflow
---

# How to use SQLFlow



* Open [the official website](https://sqlflow.gudusoft.com/) of the SQLFlow and paste your SQL script or metadata to get a nice clean lineage diagram.
* Call the [Restful API](https://github.com/sqlparser/sqlflow\_public/blob/master/api) of the SQLFlow in your own code to get data lineage metadata decoded by the SQLFlow from the SQL script.
* The [on-premise version](https://github.com/sqlparser/sqlflow\_public/blob/master/install\_sqlflow.md) of SQLflow enables you to use it on your own server to keep the data safer.

### Online Web UI

Visit [SQLFlow Cloud.](https://sqlflow.gudusoft.com)

You may paste your SQL script into the SQLFlow web page or upload the SQL file to the site. Select the correct database and then click the visualize button.

{% content-ref url="../ui/" %}
[ui](../ui/)
{% endcontent-ref %}

### Restful APIs

SQLFlow provides RESTful API, so your program can transfer data with the SQLFlow backend directly. Sending the SQL to SQLFlow backend and receive a JSON response including the data lineage and diagram model for further processing in your program.

You will need to setup the [SQLFlow on-premise version](how-to-use-sqlflow.md#on-premise-server-installation) on your server to use the API or you can connect to the [SQLFlow Cloud](https://sqlflow.gudusoft.com) to use the RESTFul API.

Check this [section](../../3.-api-docs/prerequisites.md) for more details.

{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}

### On-premise Server installation

Install SQLFlow frontend and backend on your own application/server (SQLFlow on-premise version)

To setup SQLFlow on your server, [purchase](https://www.gudusoft.com/sqlflow-on-premise-version/) and obtain a commercial license to get all those distribution files of the SQLFlow on-premise version.

{% content-ref url="../installation/" %}
[installation](../installation/)
{% endcontent-ref %}

### SDK

Integrate the frontend and backend to your data platform

Check our widget tool to onboard the sqlflow on your front application.

For the backend part, you can check the our Dlineage tool.

{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}

{% content-ref url="../java-library/" %}
[java-library](../java-library/)
{% endcontent-ref %}

### Roadmap and FAQ

{% content-ref url="../../8.-other/roadmap.md" %}
[roadmap.md](../../8.-other/roadmap.md)
{% endcontent-ref %}

{% content-ref url="../../8.-other/faq/" %}
[faq](../../8.-other/faq/)
{% endcontent-ref %}
