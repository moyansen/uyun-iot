# 数据管理

当创建模型时，转发规则选择post时，设备上报数据平台处理后，将会缓存在时序数据库，时间为3个月。客户需要及时调用数据，平台已经提供了多个纬度调用数据的api，非常方便客户调用。

缓存在平台的数据，客户可以实时查看历史数据。

![](../../.gitbook/assets/image%20%2871%29.png)

如果是数值类型的数据，平台也提供可视化看板，方便客户观察数据情况

![](../../.gitbook/assets/image%20%289%29.png)

### 配置可视化看板说明

#### 1、创建大盘

首先要创建大盘，关联相关产品，为大盘命名，以及备注

![](../../.gitbook/assets/image%20%2891%29.png)

#### 2、创建看板

首先关联设备，给看板命名，如大厅温度，选择需要具体查看的功能点，实时刷新时间，根据需要填写备注。完成后，设备有数据上报就可以实时可视化监控了。

![](../../.gitbook/assets/image%20%2828%29.png)


