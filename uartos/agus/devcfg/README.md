---
description: IoTgus屏的开发配置工作，主要是对变量显示功能以及触控/键控功能进行配置，以14.bin文件也可称为变量显示配置文件。
---

# 开发配置说明

## 显示控件配置

每个页面固定分配2KB或4KB（0x0800或0x1000）变量地址空间，每个页面最多可以配置64或128个显示功能。\(64/128条显示功能选择由CONFIG.TXT配置文件中的RC.4选择\)。

变量显示配置文件最大2MB，可以配置最多1024个页面（128条显示功能模式下最多可以配置512个页面）。相同类型的变量，存储位置越靠后，显示优先级越高。

显示控件配置完成之后，通过配置工具生成14.bin文件

一条显示变量指令由6个部分组成，具体描述请查看下表：

![](../../../.gitbook/assets/image%20%2857%29.png)

变量显示功能一览表

![](../../../.gitbook/assets/image%20%28164%29.png)

![](../../../.gitbook/assets/image%20%28118%29.png)

## 触控/键控控件功能

通过13.bin文件进行配置，故而13.bin文件也可称为触控配置文件，由配置工具生成。

该文件由一条或多条按照触/键控控功能描述的指令组成，每条指令固定占用16、32或者48个字节空间；一条触控指令由6个部分组成，具体描述请查看下表：

![](../../../.gitbook/assets/image%20%2867%29.png)

触控/键控功能一览表

![](../../../.gitbook/assets/image%20%2879%29.png)

## 

