# 云云对接

客户应用服务器可以通过云云对接的方式，请求串口云物联网平台获取设备基础信息。每分钟请求次数限制为20次。

{% api-method method="post" host="" path="/iot/v1/application/device/getdetai" %}
{% api-method-summary %}
 查询终端设备信息
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="apikey" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="device\_sn" type="string" required=true %}
device\_sn和device\_uuid二选一，查询多个可以用英文状态下的“,”隔开
{% endapi-method-parameter %}

{% api-method-parameter name="device\_uuid" type="string" required=true %}
device\_sn和device\_uuid二选一，查询多个可以英文状态下的“,”隔开
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
    "msg": "quis minim",
    "type": 87,
    "data": [
        {
            "product_uuid": "98",
            "prod_img_url": "http://dummyimage.com/400x400",
            "device_id": "28",
            "device_sn": "in aute sint ex",
            "nickname": "陆军",
            "is_online": false,
            "product_name": "少各问程己青",
            "device_uuid": "29"
        }
    ],
    "ts": 70
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

