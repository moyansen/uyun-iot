# 寄存器功能描述

### 系统版本寄存器

IoTgus屏无握手指令，在与控制系统交互使用时，两个系统之间的启动时间不一致，为确保两个系统都能正确接收到并执行相应的功能及命令，控制系统可以通过读取IoTgus屏版本号来作为握手指令。

| 寄存器地址 | 定义 | 读/写 | 长度 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| 0x00 | Version | R | 1 | 终端版本号，BCD码 |

示例：

> 控制系统发送：5A A5 03 81 00 01  
> IoTgus屏回复：5A A5 04 81 00 01 64



### 背光控制存器

IoTgus屏在运行过程中，用户可能需要自己控制终端的屏保模式，那么可以通过设置0x01寄存器的值来实现，而0x1E寄存器则保存着当前终端背光亮度值；

| 寄存器地址 | 定义 | 读/写 | 长度 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| 0x01 | Version | R/W | 1 | LCD背光亮度，0x00~0x3F |
| 0x1E | LedLm\_Now | R | 1 | 当前背光亮度值 |

示例：

控制IoTgus屏的背光亮度，下面指令把IoTgus屏背光亮度调为0

> 控制系统发送：5A A5 03 80 01 00【该值取值范围从00到3F之间】

读取当前背光亮度值

> 控制系统发送：5A A5 03 81 01 01
>
> IoTgus屏回复：5A A5 04 81 01 01 20

### 蜂鸣器控制寄存器

IoTgus屏可以通过发送指令帧控制蜂鸣器提示音实现一些简单的音频报警、提示等功能

| 寄存器地址 | 定义 | 读/写 | 长度 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| 0x02 | BzTime | W | 1 | 蜂鸣器鸣叫控制寄存器，单位 |

示例：

> 控制系统发送：5A A5 03 80 02 01【取值范围由00到FF之间的任意值】

### 触摸屏操作寄存器

通过触摸屏操作寄存器可以识别触摸屏的当前触控状态，也可以禁止。该功能仅对带有触摸屏的显示终端有效。  
  
需要通过判断IoTgus屏的触摸状态、触点坐标值，可以通过读取0x06、0x07寄存器内的值实现，但每次读取之后需要对0x05寄存器进行清零操作，否则显示终端不会自动更新触摸坐标值。

在带触摸屏的IoTgus屏上，对0x0B寄存器建议谨慎操作，如果将该寄存器设置为0x00【即对0x0B寄存器清零】，将不再执行预先定义的任何触控操作；主要应用在屏保下禁止触控，防止在屏保模式下或者是背光调暗的情况下触摸触摸屏从而引起的误操作。

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x5BC4;&#x5B58;&#x5668;&#x5730;&#x5740;</th>
      <th style="text-align:left">&#x5B9A;&#x4E49;</th>
      <th style="text-align:left">R/W</th>
      <th style="text-align:left">&#x957F;&#x5EA6;</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">0x05</td>
      <td style="text-align:left">TPFlag</td>
      <td style="text-align:left">R/W</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">
        <p>&#x7528;&#x6237;&#x8BFB;&#x53D6;&#x6570;&#x636E;&#x540E;&#x672A;&#x6E05;&#x96F6;&#x672C;&#x6807;&#x8BB0;&#xFF0C;&#x5219;&#x89E6;&#x6478;&#x5750;&#x6807;&#x4E0D;&#x518D;&#x66F4;&#x65B0;</p>
        <p>0x5A&#xFF1A;&#x89E6;&#x6478;&#x5750;&#x6807;&#x6709;&#x66F4;&#x65B0;</p>
        <p>other&#xFF1A;&#x89E6;&#x6478;&#x5750;&#x6807;&#x672A;&#x66F4;&#x65B0;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">0x06</td>
      <td style="text-align:left">TPStatus</td>
      <td style="text-align:left">R</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">
        <p>0x01&#xFF1A;&#x89E6;&#x6478;&#x5C4F;&#x9996;&#x6B21;&#x6309;&#x4E0B;
          <br
          />
        </p>
        <p>0x02&#xFF1A;&#x89E6;&#x6478;&#x5C4F;&#x6309;&#x538B;&#x7ED3;&#x675F;
          <br
          />
        </p>
        <p>0x03&#xFF1A;&#x4E00;&#x76F4;&#x6309;&#x538B;&#x4E2D;
          <br />
        </p>
        <p>other&#xFF1A;&#x65E0;&#x6548;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">0x07</td>
      <td style="text-align:left">TPPosition</td>
      <td style="text-align:left">R</td>
      <td style="text-align:left">4</td>
      <td style="text-align:left">&#x89E6;&#x6478;&#x6309;&#x538B;&#x5750;&#x6807;&#x4F4D;&#x7F6E;&#xFF1A;Xh
        Xl Yh Yl</td>
    </tr>
    <tr>
      <td style="text-align:left">0x0B</td>
      <td style="text-align:left">TPCEnable</td>
      <td style="text-align:left">R/W</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">
        <p>0x00&#xFF1A;&#x7981;&#x6B62;&#x89E6;&#x63A7;&#x529F;&#x80FD;
          <br />
        </p>
        <p>other&#xFF1A;&#x4F7F;&#x80FD;&#x89E6;&#x63A7;&#x529F;&#x80FD;&#xFF0C;&#x4E0A;&#x7535;&#x9ED8;&#x8BA4;&#x4E3A;0xFF</p>
      </td>
    </tr>
  </tbody>
</table>

获取触控功能状态

> 控制系统发送：5A A5 03 81 0B 01  
> IoTgus屏回复：5A A5 04 81 0B 01 00，表示该显示终端触控功能已经被禁用  
> IoTgus屏回复：5A A5 04 81 0B 01 XX【XX值的范围位\[01 ~ FF\]之间的任意数值】”则表示该显示终端触控功能已经使能

禁止/使能触控功能

> 控制系统发送禁止触控功能指令：5A A5 03 80 0B 00\|  
> 控制系统发送使能触控功能指令：5A A5 03 80 0B XX【XX值可以选择从00 到FF之间的任意数值】

读取触控操作的状态、触控坐标值

> 控制系统发送：5A A5 03 81 05 06  
> IoTgus屏回复：5A A5 09 81 05 06 5A 02 01 3C 01 5D

如果需要再次读取触点坐标值时，需要将0x06寄存器中的值清零，显示终端才会再次更新0x07寄存器中的值，可使用以下命令交互

> 控制系统发送：5A A5 03 81 05 06 5A A5 03 80 05 00”读取触控点坐标值的及清零0x05寄存器值  
> IoTgus屏回复：5A A5 09 81 05 06 5A 02 01 CE 01 A7

### 系统运行时间寄存器

系统在正常工作以后会自动生成一个时间，该时间为系统运行时间，格式为BCD码

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x5BC4;&#x5B58;&#x5668;&#x5730;&#x5740;</th>
      <th style="text-align:left">&#x5B9A;&#x4E49;</th>
      <th style="text-align:left">&#x8BFB;/&#x5199;</th>
      <th style="text-align:left">&#x957F;&#x5EA6;</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">0x0C</td>
      <td style="text-align:left">RunTime</td>
      <td style="text-align:left">R</td>
      <td style="text-align:left">4</td>
      <td style="text-align:left">
        <p>&#x4E0A;&#x7535;&#x8FD0;&#x884C;&#x65F6;&#x95F4;&#xFF0C;BCD&#x7801;&#xFF0C;&#x683C;&#x5F0F;&#xFF1A;&#x65F6;&#xFF1A;&#x5206;&#xFF1A;&#x79D2;
          <br
          />
        </p>
        <p>&#x793A;&#x4F8B;&#xFF1A;9999:59:59</p>
      </td>
    </tr>
  </tbody>
</table>

> 控制系统发送：5A A5 03 81 0C 04   
> IoTgus屏回复：5A A5 07 81 0C 04 96 00 57 48

### 配置寄存器操作

IoTgus屏可以通过串口发送命令修改或者读取R0~RC寄存器的参数，操作时，可以所有寄存器连续一起操作，也可以逐个寄存器操作。关于每个寄存器的说明请参考[系统配置文件说明](https://docs.uyun-iot.cn/iot/terminal/iotgus/syscfg#xi-tong-can-shu-pei-zhi-wen-jian-configtxt)。

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x5BC4;&#x5B58;&#x5668;&#x5730;&#x5740;</th>
      <th style="text-align:left">&#x5B9A;&#x4E49;</th>
      <th style="text-align:left">R/W</th>
      <th style="text-align:left">&#x957F;&#x5EA6;</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">0x10</td>
      <td style="text-align:left">TPFlag</td>
      <td style="text-align:left">R</td>
      <td style="text-align:left">13</td>
      <td style="text-align:left">TF&#x5361;&#x914D;&#x7F6E;&#x5BC4;&#x5B58;&#x5668;&#x7684;&#x6620;&#x5C04;R0
        ~ RC</td>
    </tr>
    <tr>
      <td style="text-align:left">0x1D</td>
      <td style="text-align:left">TPStatus</td>
      <td style="text-align:left">W</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">
        <p>&#x91CD;&#x8BBE;R1 ~ RC&#x5BC4;&#x5B58;&#x5668;&#x6807;&#x5FD7;</p>
        <p>0x5A&#xFF1A;R1 ~ RC&#x91CD;&#x65B0;&#x8BBE;&#x7F6E;&#xFF0C;&#x540C;&#x65F6;&#x4FDD;&#x5B58;
          <br
          />
        </p>
        <p>0xA5&#xFF1A;R1 ~ RC&#x91CD;&#x65B0;&#x8BBE;&#x7F6E;&#xFF0C;&#x4F46;&#x4E0D;&#x4FDD;&#x5B58;</p>
      </td>
    </tr>
  </tbody>
</table>

读取配置寄存器信息

> 控制系统发送：5A A5 03 81 10 0D  
> IoTgus屏回复：5A A5 10 81 10 0D 03 07 0C 5A FF FF 3F 04 03 FF A5 FF 00，通过查询寄存器位置，可以判断该数据帧内的每个字节所代表的意义。

临时修改配置寄存器信息，可实现功能例如在已经开启了屏保模式情况下，需要临时变更屏保等待时间：

> 控制系统发送：5A A5 03 80 18 20 5A A5 03 80 1D A5

修改配置寄存器信息并掉电保存，如修改刷新频率

> 控制系统发送：5A A5 03 80 12 0B 5A A5 03 80 1D 5A

### 时钟寄存器

IoTgus屏自带时钟功能，用户可以通过串口读取，也可以通过串口进行时钟的修正和校准。时钟信息保存在0x20 ~ 0x27寄存器内，其数据格式为BCD码格式。

| 寄存器地址 | 定义 | R/W | 长度 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| 0x1F | RtcComAdj | R | 1 | 0x5A表示重新设置时钟，终端执行后清零 |
| 0x20 | RtcNow | R/W | 7 | YY:MM:DD:WW:HH:MM:SS |

读取时钟信息，日历\(YY:MM:DD:WW:HH:MM:SS\)

> 控制系统发送：5A A5 03 81 20 07  
> IoTgus屏回复：5A A5 0A 81 20 07 05 02 13 00 13 05 00

读取时钟信息，读取时间\(HH:MM:SS\)

> 控制系统发送：5A A5 03 81 24 03  
> IoTgus屏回复：5A A5 06 81 24 03 13 07 16

校准时钟，用0x80指令将0x1F寄存器值设置为0x5A，并给0x20开始的寄存器写入需要校准的时间值，即可实现系统时间校准，例如将系统时间设置为“2016-03-09 16:18:30”，校准时钟时，只需要改写公历的年、月、日、时、分、秒即可，星期信息显示终端会自动修正。

> 控制系统发送：5A A5 0A 80 1F 5A 16 03 09 00 16 18 30

### 字库空间数据操作

IoTgus屏的第64 ~ 127号字库（共计64个字库，16MB存储空间）可以通过指令把字库数据读取到变量存储空间中，如果用户系统需要该信息可以通过0x83指令再从变量存储空间中读取。

| 地址 | 定义 | 读/写 | 长度 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| 0x40 | EnLibOP | R/W | 1 | 0x5A表示使能字库存储单元操作，终端执行后清零 |
| 0x41 | LibOPMode | W | 1 | 0xA0：将制定字库空间的数据写到变量存储空间 |
| 0x42 | LibID | W | 1 | 字库索引号，范围0x40 ~ 0x7F |
| 0x43 | LibAddress | W | 3 | 预读取字库空间的首地址，范围0x000000 ~ 0x01FFFF |
| 0x46 | VP | W | 2 | 预写入变量空间的首地址，范围0x0000 ~ 0x6FFF |
| 0x48 | OPLength | W | 2 | 预读取的数据长度，范围0x0001 ~ 0x6FFF |

如需要从第64号字库的0x000000地址开始读取4KW\(0x1000\)的数据到变量空间0x1000开始的位置：

> 控制系统发送：5A A5 0C 80 40 5A 40 00 00 00 10 00 10 00

### 键控寄存器

IoTgus屏不支持键盘接口，但实际使用过程中需要使用键盘或者按键操作，IoTgus屏系统提供了0x4F\(键控处理\)寄存器，方便用户使用键盘或者键码来控制执行预先定义好的触控进程。用户在操作过程中只需要将键码写入0x4F寄存器，屏则会响应触控配置文件\(13触控配置文件.bin\)描述的功能。

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x5BC4;&#x5B58;&#x5668;&#x5730;&#x5740;</th>
      <th style="text-align:left">&#x5B9A;&#x4E49;</th>
      <th style="text-align:left">R/W</th>
      <th style="text-align:left">&#x957F;&#x5EA6;</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">0x4F</td>
      <td style="text-align:left">KeyCode</td>
      <td style="text-align:left">W</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">
        <p>&#x89E6;&#x63A7;&#x952E;&#x7801;&#xFF0C;&#x7528;&#x4E8E;&#x51FA;&#x53D1;13&#x89E6;&#x63A7;&#x6587;&#x4EF6;
          <br
          />&#x6709;&#x6548;&#x503C;&#xFF1A;0x01 ~ 0xFF&#xFF1B;0x00&#x8868;&#x793A;&#x65E0;&#x6548;</p>
        <p>IoTgus&#x5C4F;&#x5904;&#x7406;&#x952E;&#x7801;&#x4E4B;&#x540E;&#x4F1A;&#x81EA;&#x52A8;&#x6E05;&#x96F6;&#x952E;&#x7801;&#x5BC4;&#x5B58;&#x5668;</p>
      </td>
    </tr>
  </tbody>
</table>

	如果在触控配置文件内定义了在第10号页面通过键码0x01进入数据录入界面，那么当屏在第10号页面时，向屏发送指令帧“5A A5 03 80 4F 01”，则屏响应一次键码触发功能并自动进入数据录入界面。  
键码触发与触摸屏触发是可以并行触发的，故可以同时使用。

### WAV音频播放寄存器

IoTgus屏，有的支持音频文件播放功能，用户可以通过0x80指令写0x50 ~ 0x54寄存器实现WAV格式的音频文件的播放、音量调节。

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x5BC4;&#x5B58;&#x5668;&#x5730;&#x5740;</th>
      <th style="text-align:left">&#x5B9A;&#x4E49;</th>
      <th style="text-align:left">&#x5EA6;/&#x5199;</th>
      <th style="text-align:left">&#x957F;&#x5EA6;</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">0x50</td>
      <td style="text-align:left">PlayMusic</td>
      <td style="text-align:left">W</td>
      <td style="text-align:left">3</td>
      <td style="text-align:left">
        <p>&#x64AD;&#x653E;&#x9884;&#x7F6E;&#x7684;&#x97F3;&#x9891;&#x6587;&#x4EF6;&#xFF1B;&#x683C;&#x5F0F;&#xFF1A;0x5A
          PlayStartID PlayNum
          <br />
        </p>
        <p>0x5A&#xFF1A;&#x4F7F;&#x80FD;&#x97F3;&#x9891;&#x64AD;&#x653E;&#x529F;&#x80FD;
          <br
          />
        </p>
        <p>PlayStartID&#xFF1A;&#x64AD;&#x653E;&#x97F3;&#x9891;&#x6587;&#x4EF6;&#x5F00;&#x59CB;&#x6BB5;&#x7D22;&#x5F15;&#x53F7;
          <br
          />
        </p>
        <p>PlayNum&#xFF1A;&#x64AD;&#x653E;&#x97F3;&#x9891;&#x6587;&#x4EF6;&#x7684;&#x6BB5;&#x6570;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">0x53</td>
      <td style="text-align:left">VolumeAdj</td>
      <td style="text-align:left">W</td>
      <td style="text-align:left">2</td>
      <td style="text-align:left">
        <p>&#x8C03;&#x6574;&#x97F3;&#x9891;&#x64AD;&#x653E;&#x7684;&#x97F3;&#x91CF;&#xFF1B;&#x683C;&#x5F0F;&#xFF1A;0x5A
          VOL
          <br />
        </p>
        <p>0x5A&#xFF1A;&#x4F7F;&#x80FD;&#x97F3;&#x9891;&#x64AD;&#x653E;&#x97F3;&#x91CF;&#x8C03;&#x6574;&#x529F;&#x80FD;
          <br
          />
        </p>
        <p>VOL&#xFF1A;&#x9884;&#x8C03;&#x6574;&#x7684;&#x97F3;&#x91CF;&#x6570;&#x503C;&#xFF1B;&#x97F3;&#x91CF;&#x4E3A;VOL/64&#xFF0C;&#x9ED8;&#x8BA4;&#x503C;&#x662F;64&#x3002;</p>
      </td>
    </tr>
  </tbody>
</table>

如播放一段音频音，假设音频文件占用了从第2段到第6段音频存储空间，需要以100％音量播放该段音频数据，则

> 控制系统发送：5A A5 07 80 50 5A 02 05 5A 40

如需要停止当前语音播放，只需要将播放指令帧中的播放段数设置为00即可，

> 控制板发送：5A A5 05 80 50 5A 02 00

如只需要调整播放的音量，只需要设置0x53及0x54寄存器，如需要将音量调整为80％

> 控制板发送：5A A5 04 80 53 5A 33

### 数据库寄存器

数据库是IoTgus屏的图片存储区域中的一块连续存储区域，空间大小和位置可由用户控制。

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x5BC4;&#x5B58;&#x5668;&#x5730;&#x5740;</th>
      <th style="text-align:left">&#x5B9A;&#x4E49;</th>
      <th style="text-align:left">&#x5EA6;/&#x5199;</th>
      <th style="text-align:left">&#x957F;&#x5EA6;</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">0x56</td>
      <td style="text-align:left">EnDBLOP</td>
      <td style="text-align:left">R/W</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">0x5A&#x8868;&#x793A;&#x4F7F;&#x80FD;&#x5B57;&#x5E93;&#x5B58;&#x50A8;&#x5355;&#x5143;&#x64CD;&#x4F5C;&#xFF0C;&#x7EC8;&#x7AEF;&#x6267;&#x884C;&#x540E;&#x6E05;&#x96F6;</td>
    </tr>
    <tr>
      <td style="text-align:left">0x57</td>
      <td style="text-align:left">OPMode</td>
      <td style="text-align:left">W</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">
        <p>0x50&#xFF1A;&#x5C06;&#x53D8;&#x91CF;&#x5B58;&#x50A8;&#x7A7A;&#x95F4;&#x7684;&#x6570;&#x636E;&#x5199;&#x5165;&#x6570;&#x636E;&#x5B58;&#x50A8;&#x7A7A;&#x95F4;
          <br
          />
        </p>
        <p>0xA0&#xFF1A;&#x5C06;&#x6570;&#x636E;&#x5B58;&#x50A8;&#x7A7A;&#x95F4;&#x7684;&#x6570;&#x636E;&#x8BFB;&#x53D6;&#x5230;&#x53D8;&#x91CF;&#x5B58;&#x50A8;&#x7A7A;&#x95F4;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">0x58</td>
      <td style="text-align:left">DBLAddress</td>
      <td style="text-align:left">W</td>
      <td style="text-align:left">4</td>
      <td style="text-align:left">&#x6570;&#x636E;&#x5E93;&#x7A7A;&#x95F4;&#x5B57;&#x5730;&#x5740;&#xFF0C;0x00000000
        ~ 0x01C1FFFF&#xFF0C;&#x6700;&#x5927;450MW&#xFF08;900MB&#xFF0C;&#x53D6;&#x51B3;&#x4E8E;&#x5185;&#x6838;
        Flash &#x60C5;&#x51B5;&#xFF09;&#x6570;&#x636E;&#x5E93;&#x7A7A;&#x95F4;&#x3002;
        <br
        />&#x6570;&#x636E;&#x5E93;&#x4ECE;&#x7269;&#x7406;&#x5B58;&#x50A8;&#x7A7A;&#x95F4;&#x7684;&#x7B2C;64MB&#x5F00;&#x59CB;&#x5B58;&#x50A8;&#xFF0C;&#x4E0E;&#x56FE;&#x7247;&#x5B58;&#x50A8;&#x5668;&#x7A7A;&#x95F4;&#x6709;&#x91CD;&#x5408;&#xFF0C;&#x6BCF;&#x4E2A;&#x6570;&#x636E;&#x5B58;&#x50A8;&#x5668;&#x5360;&#x636E;2Byte&#x7269;&#x7406;&#x5B58;&#x50A8;&#x5668;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">0x5C</td>
      <td style="text-align:left">VP</td>
      <td style="text-align:left">W</td>
      <td style="text-align:left">2</td>
      <td style="text-align:left">&#x6307;&#x5B9A;&#x53D8;&#x91CF;&#x5B58;&#x50A8;&#x5668;&#x7A7A;&#x95F4;&#x7684;&#x6570;&#x636E;&#x5E93;&#x64CD;&#x4F5C;&#x9996;&#xFF08;&#x5B57;&#xFF09;&#x5730;&#x5740;&#xFF0C;&#x8303;&#x56F4;0x0000
        ~ 0x6FFF</td>
    </tr>
    <tr>
      <td style="text-align:left">0x5E</td>
      <td style="text-align:left">OPLength</td>
      <td style="text-align:left">W</td>
      <td style="text-align:left">2</td>
      <td style="text-align:left">&#x9884;&#x8BFB;&#x53D6;&#x7684;&#x6570;&#x636E;&#x957F;&#x5EA6;&#xFF0C;&#x8303;&#x56F4;0x0001
        ~ 0x6FFF</td>
    </tr>
  </tbody>
</table>



