# User Interface

Once you have the `userid` and `secret key` the first API need to call is:

```
/gspLive_backend/user/generateToken
```

This API will return a temporary token which is required in other APIs.

#### Generate user token for restful api

{% swagger src="../../swagger/swagger.yaml" path="/user/generateToken" method="post" %}
[swagger.yaml](../../swagger/swagger.yaml)
{% endswagger %}

[**Try it out!**](../swagger-ui.md)****
