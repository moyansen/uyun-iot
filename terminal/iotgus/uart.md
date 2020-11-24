# 串口通信说明

## 串口通信

IoTgus终端（下面称为终端）与客户控制系统通信，是采用异步、全双工串口（UART）的串口通信，模式为 8n1（即每个数据传送采用十个位，包括 1 个起始 位，8 个数据位，1 个停止位），通信电平可采用TTL、RS232 或 RS485 三种式。 

串口的所有数据都是 16 进制（HEX）格式；对于字型（2 字节）数据，总是采用高字节先传送（MSB） 方式，如 0x1234 先传送 0x12。 

## 通信协议

### 协议结构

串口通信的数据帧结构，如下表所示：

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x5B57;&#x6BB5;</th>
      <th style="text-align:left">&#x957F;&#x5EA6;&#xFF08;&#x5B57;&#x8282;&#xFF09;</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">&#x5E27;&#x5934;</td>
      <td style="text-align:left">2</td>
      <td style="text-align:left">&#x53EF;&#x4EE5;&#x81EA;&#x5B9A;&#x4E49;&#xFF0C;&#x5982;0x5AA5</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x957F;&#x5EA6;</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">&#x5305;&#x62EC;&#x6307;&#x4EE4;&#x3001;&#x6709;&#x6548;&#x6570;&#x636E;&#x548C;&#x6821;&#x9A8C;</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x6307;&#x4EE4;</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">
        <p>0x80&#xFF1A;&#x5199;&#x5BC4;&#x5B58;&#x5668;&#x64CD;&#x4F5C;</p>
        <p>0x81&#xFF1A;&#x8BFB;&#x5BC4;&#x5B58;&#x5668;&#x64CD;&#x4F5C;</p>
        <p>0x82&#xFF1A;&#x5199;&#x53D8;&#x91CF;&#x5730;&#x5740;&#x64CD;&#x4F5C;</p>
        <p>0x83&#xFF1A;&#x8BFB;&#x53D8;&#x91CF;&#x5730;&#x5740;&#x64CD;&#x4F5C;</p>
        <p>0x84&#xFF1A;&#x5199;&#x66F2;&#x7EBF;&#x64CD;&#x4F5C;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#x6570;&#x636E;</td>
      <td style="text-align:left">n</td>
      <td style="text-align:left">&#x627F;&#x8F7D;&#x6570;&#x636E;</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x6821;&#x9A8C;</td>
      <td style="text-align:left">2</td>
      <td style="text-align:left">&#x9ED8;&#x8BA4;&#x4E0D;&#x6821;&#x9A8C;&#xFF0C;&#x53EF;&#x914D;&#x7F6E;&#x5F00;&#x542F;&#x6821;&#x9A8C;&#x529F;&#x80FD;</td>
    </tr>
  </tbody>
</table>

> 每帧数据能够传输的最大有效数据长度为240 个字节（不包含CRC 校验）或242 个字节（包含CRC 校验）。 CRC 校验不包括帧头和数据长度，仅针对指令和数据，采用CRC-16（算子为：X16+X15+X2+1，初始值为0xFFFF）。

### 指令说明

**写寄存器操作（0x80）**

| 字段 | 长度Byte | 说明 | 示例 |
| :--- | :--- | :--- | :--- |
| 帧头 | 2 | 自定义 | 0x5AA5 |
| 长度 | 1 | 指令+寄存器+有效数据+校验 | 0x04（无校验），0x06（有校验） |
| 指令 | 1 | 0x80 | 0x80 |
| 寄存器 | 1 | 范围0x00~0xFF | 0x03 |
| 有效数据 | n | 待操作的数据 | 0x0001 |
| 校验 | 2 | CRC16，默认不校验，可配置开启校验功能 | 0x2418 |

**读寄存器操作（0x81）**

用户操作读寄存器操作后，系统会响应返回所读取的寄存器数据

读取指令如下所示

| 字段 | 长度Byte | 说明 | 示例 |
| :--- | :--- | :--- | :--- |
| 帧头 | 2 | 自定义 | 0x5AA5 |
| 长度 | 1 | 指令+寄存器+读取寄存器个数+（校验） | 0x03（无校验），0x05（有校验） |
| 指令  | 1 | 0x81 | 0x81 |
| 寄存器 | 1 | 范围0x00~0xFF | 0x03 |
| 寄存器个数 | 1 | 需要读取的寄存器个数 | 0x02 |
| 校验 | 2 | CRC16，默认不校验，可配置开启校验功能 | 0xD9A0 |

响应指令如下所示

| 字段 | 长度Byte | 说明 | 示例 |
| :--- | :--- | :--- | :--- |
| 帧头 | 2 | 自定义 | 0x5AA5 |
| 长度 | 1 | 指令+寄存器+寄存器个数+（校验） | 0x05（无校验），0x07（有校验） |
| 指令  | 1 | 0x81 | 0x81 |
| 寄存器 | 1 | 范围0x00~0xFF | 0x03 |
| 寄存器个数 | 1 | 需要读取的寄存器个数 | 0x02 |
| 响应数据 | n | 根据读取的寄存器返回的数据 | 0x0001 |
| 校验 | 2 | CRC16，默认不校验，可配置开启校验功能 | 0x5A78 |

**写变量地址操作（0x82）**

| 字段 | 长度Byte | 说明 | 示例 |
| :--- | :--- | :--- | :--- |
| 帧头 | 2 | 自定义 | 0x5AA5 |
| 长度 | 1 | 指令+起始变量地址+有效数据+校验 | 0x05（无校验），0x07（有校验） |
| 指令 | 1 | 0x82 | 0x82 |
| 起始变量地址 | 2 | 范围0x0000~0xFFFF | 0x0010 |
| 有效数据 | n | 待操作的数据 | 0x0001 |
| 校验 | 2 | CRC16，默认不校验，可配置开启校验功能 | 0x1B9C |

**读变量地址操作（0x83）**

**控制板发送**

| 字段 | 长度Byte | 说明 | 示例 |
| :--- | :--- | :--- | :--- |
| 帧头 | 2 | 自定义 | 0x5AA5 |
| 长度 | 1 | 指令+起始变量地址+变量地址个数+（校验） | 0x04（无校验），0x06（有校验） |
| 指令  | 1 | 0x83 | 0x83 |
| 起始变量地址 | 1 | 范围0x0000~0xFFFF | 0x0010 |
| 变量地址个数 | 1 | 需要读取的变量地址个数 | 0x01 |
| 校验 | 2 | CRC16，默认不校验，可配置开启校验功能 | 0xA0E5 |

**IoTgus屏响应**

| 字段 | 长度Byte | 说明 | 示例 |
| :--- | :--- | :--- | :--- |
| 帧头 | 2 | 自定义 | 0x5AA5 |
| 长度 | 1 | 指令+起始变量地址+变量地址个数+（校验） | 0x06（无校验），0x08（有校验） |
| 指令  | 1 | 0x83 | 0x83 |
| 起始变量地址 | 1 | 范围0x0000~0xFFFF | 0x0010 |
| 变量地址个数 | 1 | 需要读取的变量地址个数 | 0x01 |
| 响应数据 | n | 根据读取的变量地址个数返回的数据 | 0x0001 |
| 校验 | 2 | CRC16，默认不校验，可配置开启校验功能 | 0x288B |

**写曲线操作（0x84）**

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x5B57;&#x6BB5;</th>
      <th style="text-align:left">&#x957F;&#x5EA6;Byte</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
      <th style="text-align:left">&#x793A;&#x4F8B;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">&#x5E27;&#x5934;</td>
      <td style="text-align:left">2</td>
      <td style="text-align:left">&#x81EA;&#x5B9A;&#x4E49;</td>
      <td style="text-align:left">0x5AA5</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x957F;&#x5EA6;</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">&#x6307;&#x4EE4;+&#x901A;&#x9053;+&#x6709;&#x6548;&#x6570;&#x636E;+&#x6821;&#x9A8C;</td>
      <td
      style="text-align:left">0x04&#xFF08;&#x65E0;&#x6821;&#x9A8C;&#xFF09;&#xFF0C;0x06&#xFF08;&#x6709;&#x6821;&#x9A8C;&#xFF09;</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x6307;&#x4EE4;</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">0x84</td>
      <td style="text-align:left">0x84</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x901A;&#x9053;</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">
        <p>&#x6309;&#x4F4D;&#x8BA1;&#x7B97;&#xFF0C;
          <br />&#x901A;&#x9053;1&#x53D6;&#x503C;&#x4E3A;00000001B</p>
        <p>&#x901A;&#x9053;2&#x53D6;&#x503C;&#x4E3A;00000010B</p>
        <p>&#x901A;&#x9053;1&#x548C;2&#x53D6;&#x503C;&#x4E3A;00000011B</p>
      </td>
      <td style="text-align:left">0x01</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x6709;&#x6548;&#x6570;&#x636E;</td>
      <td style="text-align:left">n</td>
      <td style="text-align:left">&#x663E;&#x793A;&#x66F2;&#x7EBF;&#x7684;&#x6570;&#x636E;</td>
      <td style="text-align:left">0x0001</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x6821;&#x9A8C;</td>
      <td style="text-align:left">2</td>
      <td style="text-align:left">CRC16&#xFF0C;&#x9ED8;&#x8BA4;&#x4E0D;&#x6821;&#x9A8C;&#xFF0C;&#x53EF;&#x914D;&#x7F6E;&#x5F00;&#x542F;&#x6821;&#x9A8C;&#x529F;&#x80FD;</td>
      <td
      style="text-align:left">0xD4B8</td>
    </tr>
  </tbody>
</table>

示例中指令实现数据1写入IoTgus屏变量中，IoTgus将会根据相应的配置做相应的动作 

> 无校验：5AA5 04 84 01 0001 
>
> 有校验：5AA5 06 84 01 0001 D4B8

