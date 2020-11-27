# 按功能组查询数据

{% api-method method="post" host="https://api.cakes.com" path="/iot/v1/application/group/property/timeminutes" %}
{% api-method-summary %}
查询某功能组功能点N分钟的数据
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="apikey" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="product\_uuid" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="device\_uuid" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="groupid" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="minutes" type="integer" required=true %}
The API do its best to find a cake matching the provided recipe.
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "code": 200,
    "msg": "OK",
    "type": 32,
    "data": [
        {
            "groupid": "a017b6f46745",
            "int16": 0,
            "int32": 0,
            "time": "2020-11-26T17:41:29.38857378Z",
            "ts": 1606412488
        },
        {
            "groupid": "a017b6f46745",
            "int16": 68,
            "int32": 0,
            "time": "2020-11-26T17:32:59.501447577Z",
            "ts": 1606411979
        }
    ],
    "ts": 1606445604698
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://api.cakes.com" path="/iot/v1/customer/application/group/property/timedays" %}
{% api-method-summary %}
查询某功能组功能点N天数据
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="apikey" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="product\_uuid" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="device\_uuid" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="groupid" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="days" type="integer" required=true %}

{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "code": 200,
    "msg": "OK",
    "type": 32,
    "data": [
        {
            "groupid": "a017b6f46745",
            "int16": 0,
            "int32": 0,
            "time": "2020-11-26T17:41:29.38857378Z",
            "ts": 1606412488
        },
        {
            "groupid": "a017b6f46745",
            "int16": 68,
            "int32": 0,
            "time": "2020-11-26T17:32:59.501447577Z",
            "ts": 1606411979
        }
    ],
    "ts": 1606445604698
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://api.cakes.com" path="/iot/v1/customer/application/group/property/limit" %}
{% api-method-summary %}
查询某功能组功能点N个数据
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="apikey" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="product\_uuid" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="device\_uuid" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="groupid" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="page" type="integer" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="limit" type="integer" required=true %}

{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "code": 200,
    "msg": "OK",
    "type": 32,
    "data": [
        {
            "groupid": "a017b6f46745",
            "int16": 0,
            "int32": 0,
            "time": "2020-11-26T17:41:29.38857378Z",
            "ts": 1606412488
        },
        {
            "groupid": "a017b6f46745",
            "int16": 68,
            "int32": 0,
            "time": "2020-11-26T17:32:59.501447577Z",
            "ts": 1606411979
        }
    ],
    "ts": 1606445604698
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

