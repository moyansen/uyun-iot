# 远程调用

第三方应用服务器通过远程调用的restful接口，很便捷的实现远程控制设备。远程调用有两种，分别是异步调用与同步调用。

异步调用交互流程图如下所示

![](../../.gitbook/assets/image%20%28123%29.png)



{% api-method method="post" host="" path="/iot/v1/application/device/rpc/async" %}
{% api-method-summary %}
新版异步调用api 
{% endapi-method-summary %}

{% api-method-description %}
异步调用是指第三方服务通过异步调用接口，给设备下发命令，接口响应的结果并不是设备返回的结果，而设备上报的结果需要通过另外的方式（如数据推送、消息推送、数据调用）获得设备被调用之后的结果。  
交互流程：
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="apikey" type="string" required=true %}
每个客户都有唯一apikey，在账号信息下可以查询，要注意保密 
{% endapi-method-parameter %}

{% api-method-parameter name="product\_uuid" type="string" required=true %}
创建产品时，平台自动生成
{% endapi-method-parameter %}

{% api-method-parameter name="device\_uuid" type="string" required=true %}
设备成功注册后，平台自动生成
{% endapi-method-parameter %}

{% api-method-parameter name="method" type="string" required=true %}
根据模型而定，可查看规则文件
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="datapoint" type="string" required=true %}
 根据功能点而定
{% endapi-method-parameter %}

{% api-method-parameter name="method" type="string" required=true %}
 根据模型而定，可查看规则文件
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
成功调用后，平台会响应参数，其中的msgid，客户服务器需要记住，用于回调匹配消息
{% endapi-method-response-example-description %}

```
{
    "code": 200,
    "msg": "OK",
    "type": 34,
    "data": {
        "msgid": "2a16LUTGsErS",
        "topic": "sub-raw-private"
    },
    "ts": 1606101246445
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="" path="/iot/v1/application/device/send/property/object" %}
{% api-method-summary %}
 老版异步调用api
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="apikey" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="product\_uuid" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="deivce\_uuid" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="cmd" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="msgid" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
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

###  <a id="ern7M"></a>

