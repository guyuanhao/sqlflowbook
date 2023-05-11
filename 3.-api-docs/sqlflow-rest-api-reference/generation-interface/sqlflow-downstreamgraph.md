# /sqlflow/downstreamGraph

Retrieve the upstream data lineage for data elements in [_**regular Job**_](../../../1.-introduction/getting-started/different-modes-in-gudu-sqlflow/job-mode.md#regular-job). This API corresponds to [the downstream/upstream feature](../../../1.-introduction/ui/schema.md#to-upstream-to-downstream) in SQLFlow UI.

### &#x20;Get downstream data lineage in Json

```
/sqlflow/generation/sqlflow/downstreamGraph
```

{% swagger src="../../../.gitbook/assets/swagger.yaml" path="/sqlflow/generation/sqlflow/downstreamGraph" method="post" %}
[swagger.yaml](../../../.gitbook/assets/swagger.yaml)
{% endswagger %}

### Get downstream data lineage image

```
/sqlflow/generation/sqlflow/downstreamGraph/image
```

{% swagger src="../../../.gitbook/assets/swagger.yaml" path="/sqlflow/generation/sqlflow/downstreamGraph/image" method="post" %}
[swagger.yaml](../../../.gitbook/assets/swagger.yaml)
{% endswagger %}

Sample:

```bash
curl --location 'https://<SQLFlow URL>/gspLive_backend/sqlflow/generation/sqlflow/downstreamGraph/image' \
--header 'accept: image/*' \
--form 'userId="gudu|0123456789"' \
--form 'sessionId="85b5119f83fcfefa93136e79dc05f2f61efe3b75e6a2b733568e0879c24f0c08_1680615728918"' \
--form 'dbvendor="dbvmssql"' \
--form 'jobId="6def00e8796e4c20ba216826c0ab5b73"' \
--form 'tableNamePattern="dwdb.dbo.tbl_headblockersummary"'
```

<figure><img src="../../../.gitbook/assets/04051.png" alt=""><figcaption></figcaption></figure>
