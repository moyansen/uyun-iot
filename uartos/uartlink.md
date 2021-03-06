# UartLink应用开发指南

UartLink智能模块系统，基于gus协议体系、依托串口云物联网平台，实现多网络模式（2G、4G、NB-IoT、WiFi或者有线）统一接入与使用，客户只需要通过调用相关gus协议的命令，即实现设备上云。UartLink智能网络模块，帮助熟悉gus串口屏的客户快速低沉本构建/升级为物联网应用产品，实现统一接入与使用，客户只需要通过调用相关命令，即实现设备上云。

![](../.gitbook/assets/image%20%285%29.png)

## 1、串口通信约定 <a id="0eCdt"></a>

串口通信均采用异步、全双工模式。其工作属性为8n1模式，即每个字节采用10bit数据发送：1个起始位、8个数据位（低位在前，LSB）、1位停止位、无校验。

波特率：115200

## 2、指令帧结构 <a id="q7px5"></a>

显示终端通过特定的帧结构实现数据交互；该帧由四个部分组成，如下表所示：

| **帧结构** | **帧头** | **数据长度** | **指令** | **变量地址** | **数据** | **校验** |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **数据长度\(Byte\)** | 2 | 1 | 1 | 1 | N | 2 |
| **说明** | 5AA5 | 指令+变量地址+数据+校验 | 82/83 | 0000-FFFF | 数据 | 可选，CRC16 |

### 2.1 指令说明 <a id="JWtq7"></a>

#### 帧头 <a id="qvZsz"></a>

帧头固定0x5AA5，两个字节

#### 数据长度 <a id="L2yim"></a>

数据长度包括指令、变量地址、数据和校验的长度，单位为字节。CRC16校验是可选的，用户根据实际需要开启。一个字节

#### 指令 <a id="3WM6Q"></a>

指令有0x82和0x83两条指令。0x82写指令，用于操作模块参数或者上报数据；0x83读取模块参数或者平台数据下发。

#### 变量地址 <a id="x19bV"></a>

变量地址范围为0x0000-0xFFFF。其中0x0000-0x7FFF为数据交互使用，0x8000~0xFFFF为模块系统功能使用。

#### 数据

用户操作的有效数据

#### 校验

CRC16校验，对校验指令、变量地址、数据进行校验

## 3、系统功能说明 <a id="YuLqj"></a>

| **起始变量地址** | **功能定义** |
| :--- | :--- |
| 0x8000 | 模块状态 |
| 0x8010 | 模块信息 |
| 0x8020 | 模块配网 |
| 0x8030 | 模块注册 |

### 3.1 模块状态 <a id="kYAGN"></a>

用户通0x8000可以读取模块的状态，

**读取模块状态**

| **帧头** | **长度** | **指令** | **起始变量地址** | **读取长度（字）** | **CRC校验** |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 2字节 | 1字节 | 1字节 | 2字节 | 1字节 | 2字节 |

**模块返回状态**

| **帧头** | **长度** | **指令** | **起始变量地址** | **读取长度（字）** | **信号强度** | **接入平台提示** | **接入运行时间** | **IP地址** | **CRC校验（可选）** |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 2字节 | 1字节 | 1字节 | 2字节 | 1字节 | 2字节 | 2字节 | 4字节 | 18字节 | 2字节 |

信号强度：0~4  
接入平台提示：0表示未接入平台，1表示已接入平台  
接入运行时间：表示本次接入平台后的时间，与设备在线时间一致  
IP地址：WiFi模块是局域网地址，4G模块是公网IP

### 3.2 模块信息 <a id="S3pFt"></a>

**读取模块信息**

| **帧头** | **长度** | **指令** | **起始变量地址** | **读取长度（字）** | **CRC校验（可选）** |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 2字节 | 1字节 | 1字节 | 2字节 | 1字节 | 2字节 |

**模块返回信息**

| **帧头** | **长度** | **指令** | **起始变量地址** | **读取长度（字）** | **模块型号** | **软件版本** | **模块序列号** | **CRC校验（可选）** |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 2字节 | 1字节 | 1字节 | 2字节 | 1字节 | 10字节 | 6字节 | 16字节 | 2字节 |

模块型号：根据各个型号的模块而定

软件版本：UartLink系统软件版本。模块会自动更新最新版本

模块序列号：每个模块出厂前都分配唯一序列号

### 3.3 模块配网 <a id="jjtcD"></a>

**写入配网信息**

| **帧头** | **长度** | **指令** | **起始变量地址** | **配网方式** | **ssid** | **password** | **CRC校验（可选）** |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 2字节 | 1字节 | 1字节 | 2字节 | 2字节 | 15字节 | 15字节 | 2字节 |

配网方式：1-STA模式 2-SMART模式

**模块返回信息**

| **帧头** | **长度** | **指令** | **起始变量地址** | **读取长度（字）** | **配网方式** | **ssid** | **password** | **CRC校验（可选）** |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 2字节 | 1字节 | 1字节 | 2字节 | 1字节 | 2字节 | 15字节 | 15字节 | 2字节 |

### 3.4 模块注册0x8030 <a id="RyuWU"></a>

**写入注册信息**

| **帧头** | **长度** | **指令** | **起始变量地址** | **product\_auth** | **CRC校验（可选）** |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 2字节 | 1字节 | 1字节 | 2字节 | 30字节 | 2字节 |

**模块返回信息**

| **帧头** | **长度** | **指令** | **起始变量地址** | **读取长度（字）** | **product\_auth** | **CRC校验（可选）** |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 2字节 | 1字节 | 1字节 | 2字节 | 1字节 | 30字节 | 2字节 |

## 4、数据通信 <a id="nGwKN"></a>

mcu与WiFi模块进行数据通信交互，通过gus指令协议进行数据交互。首先要在平台建立物模型，根据物模型生成的规则文件，WiFi模块对上行数据需要根据规则文件进行封装payload

### 4.1 文件传输 <a id="wBWaL"></a>

待更新

### 4.2 数据点交互 <a id="SgGpH"></a>

#### 4.2.1 发布数据（0x0000~0x7FFF） <a id="sgL4u"></a>

变量地址范围0x0000~0x7FFF，用于数据通信，mcu发送数据到模块后，模块根据规则文件发布到平台。

指令格式

| **帧头** | **长度** | **指令** | **起始变量地址** | **数据** | **CRC校验（可选）** |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 2字节 | 1字节 | 1字节 | 2字节 | 240字节 | 2字节 |

**示例指令**

5AA5 07 82 1040 0000 0001

#### 4.2.2 下发数据 <a id="oqt9h"></a>

模块接收到平台下发数据

**\(1\)平台下发数据cmd为83时**

直接把para数据发送串口给设备端，如下所示5AA5 08 83 1040 02 0000 0001发送到串口给mcu

**\(2\)平台下发数据cmd为82时**

数据写入模块的缓存中，按照变量地址缓存，并根据配置发送给mcu，后续mcu还可以过来读取

把para数据发送串口给设备端，如下所示5AA5 08 83 1040 02 0000 0001发送到串口给mcu

