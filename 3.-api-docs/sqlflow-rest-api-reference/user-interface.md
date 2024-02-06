# User Interface

Once you have the `userid` and `secret key` the first API need to call is:

```
/gspLive_backend/user/generateToken
```

This API will return a temporary token which is required in other APIs.

If you are using SQLFLow On-Premise, token might not be required if you have set following flag in `/wings/sqlflow/backend/conf/gudu_sqlflow.conf`

```bash
ignore_user_token=true
```

#### Generate user token for restful api

{% swagger src="../../.gitbook/assets/swagger_with_token.yaml" path="/user/generateToken" method="post" %}
[swagger_with_token.yaml](../../.gitbook/assets/swagger_with_token.yaml)
{% endswagger %}

[**Try it out!**](../swagger-ui.md)
