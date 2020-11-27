# 数据调用

设备上报数据后，客户并不马上需要使用，平台处理后先缓存在时序数据库；平台提供了多维度进行数据调用，客户根据需要通过数据调用api调用数据。

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

{% api-method method="post" host="" path="" %}
{% api-method-summary %}
查询某个功能点最近N分钟的数据
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
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

