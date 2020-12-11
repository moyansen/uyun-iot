# 数据推送

数据推送是通过回调的方式实现，客户在平台上配置回调地址。平台通过调用客户的回调地址，把数据post给客户的业务服务器。

客户在定义回调接口时，需要遵循下面的规范

1. 回调接口统一使用post方法
2. param参数可选，目前平台只支持填写apikey
3. body请求的数据格式按照ujson格式处理
4. 收到平台的数据后，必须并严格按照规定数据格式响应

### 回调接口设计示例

> https://api.example.com/iot/v1/callback

### body格式如下

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

### 响应格式

必须把平台回调过来的msgid作为参数，要不然平台会认为回调失败

```text
{
	"code":200,
  "msgid":"23423424234"
}
```

