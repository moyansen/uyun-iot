---
description: IoT串口开发使用文档
---

# 网络配置说明

## 触控相关配置

变量地址0x8000作为网络操作功能，不同的值对应不同的功能

高字节为0x00平台接入相关，高字节为0x01网络相关，高字节为0x02数据通信相关。

| **功能模块** | **说明** |
| :--- | :--- |
|  0x0001 | 确认接入注册 |
| 0x0101-0x0108 | 选择WiFi热点 |
| 0x0109 | 搜索热点 |
| 0x010A | 接入热点模式 |
| 0x010B | 查询网模块信息 |
| 0x010C | 获取WiFi信息状态 |
| 0x0200 | 使能下载文件 |

## 查看网络状态

用于串口屏间隔5秒读取模块网络运行状态。显示设备的信号强度、接入平台提示、IP地址、接入的平台、运行时间。

| **功能** | **变量地址** | **长度** | **说明** |
| :--- | :--- | :--- | :--- |
| 信号强度 | 0x8001 | 2字节 | 信号强度0~4 |
| 接入平台提示 | 0x8002 | 2字节 | 0：掉线，1：已接入平台 |
| IP地址 | 0x8003 | 18字节 | 文本，示例192.168.0.1 |
| 在线时间 | 0x800D | 4字节 | 设备每次接入平台的时间 |
| 激活状态 | 0x800F | 2字节 | 0：未注册，1：已注册，2：MQTT账号异常 |

## 注册IoTgus终端

| **功能模块** | **变量地址** | **长度** | **说明** |
| :--- | :--- | :--- | :--- |
| 接入平台 | 0x8010 | 32（字节） | 平台生成 |
| device\_sn | 32（字节） | 出厂内置 |  |

## 查询模组信息

| **功能模块** | 变量地址 | 长度 | 说明 |
| :--- | :--- | :--- | :--- |
| 模块型号 | 0x8050 | 12（字节） |  |
| 模块序列号 | 0x8056 | 20（字节） | IMEI、WiFi使用Mac地址计算出来的码 15~17个数字 |
| 模块软件版本 | 0x8060 | 6（字节） | 数值类型 |
| 接入平台 | 0x8063 | 2（字节） | 1：接入uartcloud |

## WiFi配置相关

### WiFi配网

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>&#x529F;&#x80FD;&#x6A21;&#x5757;</b>
      </th>
      <th style="text-align:left">&#x53D8;&#x91CF;&#x5730;&#x5740;</th>
      <th style="text-align:left"><b>&#x53D8;&#x91CF;&#x5730;&#x5740;</b>
      </th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p></p>
        <p>&#x5F85;&#x63A5;&#x5165;/&#x8BBE;&#x7F6E;AP SSID</p>
      </td>
      <td style="text-align:left">0x8090</td>
      <td style="text-align:left">32&#x5B57;&#x8282;</td>
      <td style="text-align:left">
        <p>&#x5F53;&#x914D;&#x7F51;&#x65B9;&#x5F0F;&#x4E3A;station&#x65F6;&#xFF0C;&#x4E3A;&#x5F85;&#x63A5;&#x5165;&#x7684;ssid</p>
        <p>&#x5F53;&#x914D;&#x7F51;&#x65B9;&#x5F0F;&#x4E3A;ap&#x65F6;&#xFF0C;&#x4E3A;&#x5F85;&#x8BBE;&#x7F6E;&#x7684;&#x70ED;&#x70B9;ssid</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#x5F85;&#x63A5;&#x5165;/&#x8BBE;&#x7F6E;AP PSW</td>
      <td style="text-align:left">0x80A0</td>
      <td style="text-align:left">32&#xFF08;&#x5B57;&#x8282;&#xFF09;</td>
      <td style="text-align:left">
        <p>&#x5F53;&#x914D;&#x7F51;&#x65B9;&#x5F0F;&#x4E3A;station&#x65F6;&#xFF0C;&#x4E3A;&#x5F85;&#x63A5;&#x5165;&#x7684;password</p>
        <p>&#x5F53;&#x914D;&#x7F51;&#x65B9;&#x5F0F;&#x4E3A;ap&#x65F6;&#xFF0C;&#x4E3A;&#x5F85;&#x8BBE;&#x7F6E;&#x7684;&#x70ED;&#x70B9;password</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>rssi1&#x4FE1;&#x53F7;&#x5F3A;&#x5EA6;</b>
      </td>
      <td style="text-align:left"><b>0x80B0</b>
      </td>
      <td style="text-align:left"><b>2&#xFF08;&#x5B57;&#x8282;&#xFF09;</b>
      </td>
      <td style="text-align:left"><b>&#x641C;&#x7D22;&#x5230;&#x7684;ssid1</b>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>SSID1</b>
      </td>
      <td style="text-align:left"><b>0x80B1</b>
      </td>
      <td style="text-align:left"><b>30&#xFF08;&#x5B57;&#x8282;&#xFF09;</b>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#x2026;&#x2026;</td>
      <td style="text-align:left">&#x2026;&#x2026;</td>
      <td style="text-align:left">&#x2026;&#x2026;</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>SSID8&#x4FE1;&#x53F7;&#x5F3A;&#x5EA6;</b>
      </td>
      <td style="text-align:left"><b>0x8120</b>
      </td>
      <td style="text-align:left"><b>2&#xFF08;&#x5B57;&#x8282;&#xFF09;</b>
      </td>
      <td style="text-align:left"><b>&#x641C;&#x7D22;&#x5230;&#x7684;ssid8</b>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>SSID8</b>
      </td>
      <td style="text-align:left"><b>0x8121</b>
      </td>
      <td style="text-align:left"><b>30&#xFF08;&#x5B57;&#x8282;&#xFF09;</b>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#x914D;&#x7F51;&#x65B9;&#x5F0F;&#x9009;&#x62E9;</td>
      <td style="text-align:left">0x8130</td>
      <td style="text-align:left">2&#xFF08;&#x5B57;&#x8282;&#xFF09;</td>
      <td style="text-align:left">0:station&#x3001;1:smartconfig&#x3001;2:airkiss&#x3001;3:ap</td>
    </tr>
  </tbody>
</table>

### **查询WiFi状态**

| **功能模块** | 变量地址 | **变量地址** | **长度** |
| :--- | :--- | :--- | :--- |
| ssid | 0x8140 | 32（字节） | 当前接入的ssid |
| mode | 0x8150 | 2（字节） | WiFi当配网方式为station时， |
| mac | 0x8151 | 14（字节） | Mac地址 |
| ip | 0x8159 | 18（字节） |  |
| mask | 0x8162 | 18（字节） |  |
| gateway | 0x816B | 18（字节） |  |

#### 2.2.6 4G配置相关 <a id="MtS00"></a>

后续更新

## 端云数据通信

### 文件传输

| **功能模块** | **功能参数** | **变量地址** | **长度** | **说明** |
| :--- | :--- | :--- | :--- | :--- |
| 配置更新状态 | 配置类型 | 0x81B0 | 2（字节） | 未启用 |
| 配置文件名 | 0x81B1 | 30（字节） | 如22.bin |  |
| 文件大小  | 0x81C0 | 4（字节） |  |  |
| 版本 | 0x81C2 | 6（字节） |  |  |

### 数据点通信

整理需要上报云平台和云平台下发的变量地址数据点，通过在平台控制台配置模型，即可实现配置数据上报云平台，以及云端下发数据到设备。

