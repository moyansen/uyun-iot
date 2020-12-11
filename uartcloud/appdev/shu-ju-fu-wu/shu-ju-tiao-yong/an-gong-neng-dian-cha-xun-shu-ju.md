# 按功能点查询数据

{% api-method method="post" host="" path="/iot/v1/application/datapoint/property/list" %}
{% api-method-summary %}
查询产品所有的功能点
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
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
data参数是功能点，功能点就是在创建模型时定义的
{% endapi-method-response-example-description %}

```
{
	"code": 10,
	"msg": "nostrud aliquip id commodo",
	"type": 30,
	"data": [
		"key1",
		"keyn"
	],
	"ts": 25
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="" path="/iot/v1/application/datapoint/property/timeminutes" %}
{% api-method-summary %}
查询某个功能点最近N分钟的数据
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

{% api-method-parameter name="device\_uuid	" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="datapoint" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="minutes" type="integer" required=true %}
 
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
数据放在data中，以二维数组形式
{% endapi-method-response-example-description %}

```
{
	"code": 200,
	"msg": "OK",
	"type": 32,
	"data": [
		[
			"2020-11-26T16:22:28.375755681Z",
			10
		],
		[
			"2020-11-26T16:22:28.241976383Z",
			13
		]
	],
	"ts": 1606443688115
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="" path="/iot/v1/application/datapoint/property/timedays" %}
{% api-method-summary %}
查询某个功能点最近N天的数据
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="apikey" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="product\_uuid" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="device\_uuid	" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="datapoint" type="string" required=true %}

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
        [
            "2020-11-26T17:41:29.38857378Z",
            0
        ],
        [
            "2020-11-26T17:32:59.501447577Z",
            0
        ]
    ],
    "ts": 1606444344153
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="" path="/iot/v1/application/datapoint/property/limit" %}
{% api-method-summary %}
查询某个功能点最近n个数据
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

{% api-method-parameter name="datapoint" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="limit" type="string" required=true %}
需要查询的数据个数
{% endapi-method-parameter %}

{% api-method-parameter name="page" type="string" required=false %}
如果需要查询的数据个数较多，可以分页查询
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

