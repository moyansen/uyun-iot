# 数据推送

数据推送是通过回调的方式实现，客户在平台上配置回调地址。平台通过调用客户的回调地址，把数据post给客户的业务服务器。客户在定义回调接口时，需要遵循下面的规范

1、回调接口统一使用post方式

2、param参数可选，目前平台只支持填写apikey

3、body请求的数据格式如下

```text
{
	"payload": {
		"method": "",
		"profile": {
			"customer_uuid": "",
			"product_uuid": "",
			"device_uuid": ""
		},
		"datapoint": {
			"cmd": "",
			"para": {

			}
		},
		"version": "1.0.1",
		"msgid": "",
		"ts": 1599823075475
	},
	"type": "",
	"ts": 1606103322705
}
```

4、响应格式，必须把平台回调过来的msgid作为参数，要不然平台会认为回调失败

```text
{
	"code":200,
  "msgid":"23423424234"
}
```

{% api-method method="post" host="https://api.example.com/iot/v1/callback" path="" %}
{% api-method-summary %}
 回调接口示例
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="apikey" type="string" required=false %}
可选
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="" type="object" required=true %}

{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
格式如下所示，响应时必须把回调的msgid返回
{% endapi-method-response-example-description %}

```
{
	"code":200,
  "msgid":"23423424234"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

