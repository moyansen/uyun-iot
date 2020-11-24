# 系统配置说明

IoTgus屏的系统工作需要用到的文件素材文件和配置文件，其中素材文件有图片文件、音频文件、视频文件；字库文件有0号标准ASCII字库文件、变量配置文件、自定义字库文件与图标文件；配置文件有、参数配置文件、数据转发规则文件。

素材文件、字库文件、配置文件存储在IoTgus屏Flash中，掉电时不会丢失，其中的视频文件存在SD卡，IoTgus屏通过读取SD视频文件播放视频。IoTgus屏把Flash空间划分为字库空间、图片空间、音频空间、数据库空间。

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x7A7A;&#x95F4;&#x540D;&#x79F0;</th>
      <th style="text-align:left">&#x7A7A;&#x95F4;&#x5927;&#x5C0F;</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">&#x5B57;&#x5E93;&#x7A7A;&#x95F4;</td>
      <td style="text-align:left">32MB</td>
      <td style="text-align:left">&#x56FA;&#x5B9A;32MB&#x7A7A;&#x95F4;</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x56FE;&#x7247;&#x7A7A;&#x95F4;</td>
      <td style="text-align:left">
        <p>Flash&#x7A7A;&#x95F4;&#x4E3A;128MB&#xFF0C;&#x5219;&#x6700;&#x5927;&#x56FE;&#x7247;&#x7A7A;&#x95F4;&#x4E3A;96MB</p>
        <p>Flash&#x7A7A;&#x95F4;&#x4E3A;256MB&#xFF0C;&#x5219;&#x6700;&#x5927;&#x56FE;&#x7247;&#x7A7A;&#x95F4;&#x4E3A;210MB</p>
        <p>Flash&#x7A7A;&#x95F4;&#x4E3A;1GB&#xFF0C;&#x5219;&#x6700;&#x5927;&#x56FE;&#x7247;&#x7A7A;&#x95F4;&#x4E3A;932MB</p>
      </td>
      <td style="text-align:left">&#x6839;&#x636E;&#x4E0D;&#x540C;&#x7684;Flash&#x7A7A;&#x95F4;&#x5927;&#x5C0F;&#x800C;&#x5B9A;</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x97F3;&#x9891;&#x7A7A;&#x95F4;</td>
      <td style="text-align:left">8MB</td>
      <td style="text-align:left">&#x5728;&#x56FE;&#x7247;&#x7A7A;&#x95F4;&#x7684;&#x6700;&#x540E;8MB&#x7A7A;&#x95F4;&#x5212;&#x5206;</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x6570;&#x636E;&#x5E93;&#x7A7A;&#x95F4;</td>
      <td style="text-align:left">
        <p>Flash&#x7A7A;&#x95F4;&#x4E3A;256MB&#xFF0C;&#x5219;&#x6700;&#x5927;&#x6570;&#x636E;&#x5E93;&#x7A7A;&#x95F4;&#x4E3A;89MB</p>
        <p>Flash&#x7A7A;&#x95F4;&#x4E3A;1GB&#xFF0C;&#x5219;&#x6700;&#x5927;&#x6570;&#x636E;&#x5E93;&#x7A7A;&#x95F4;&#x4E3A;450MB</p>
      </td>
      <td style="text-align:left">&#x6839;&#x636E;&#x4E0D;&#x540C;&#x7684;Flash&#x7A7A;&#x95F4;&#x5927;&#x5C0F;&#x800C;&#x5B9A;</td>
    </tr>
  </tbody>
</table>

> 图片空间与数据库空间共用flash空间

## 素材文件说明

IoTGUS 通过文件编号来存放和调用素材文件的，素材文件命名均应当用阿拉伯数字开头， 通过阿拉伯数字对文件实现编号。

### 图片文件说明

图片文件的格式要求为BMP、24位色，分辨率与所选的IoTgus屏分辨率。图片命名编号从0开始，编号的范围根据IoTgus屏的存储容量而定；IoTgus屏开机时默认显示第0张图片，如果缺失第0张图片，开机后可能会显示异常。

> 示例：要将一副图片存储在IoTgus屏的第15 个图片位置，图片文件需命名为“15.bmp”“或者15\_xx.bmp”或者“15 xx.bmp”或者“015 xx.bmp”，但是不能命名为“xx 15.BMP”。

图片素材文件可通过作图软件，例如Photoshop、illustrator等设计软件制作。

### 音频文件说明

部分显示终端支持播放WAV 格式的音频文件，该功能需要硬件支持，故请查看相应的显示终端数据手册查询。 音频文件的下载与字库下载类似，命名必须是表示音频文件存储的位置的阿拉伯数字开始，如“0 关门提示.WAV”， 音频文件格式为WAV 格式、32KHz 采样频率，16bit 单声道WAV 文件。

音频文件存储在图片区域的最后部分，总计128 段、占用8MB 的Flash 空间。

### 视频视频说明

IoTgus屏支持播放视频功能，视频文件存储在SD卡中，视频格式为avi

## 字库文件说明

IoTgus屏从Flash空间中，固定的划分出32MB存储空间作为字库空间，同时把这32MB空间分割成128 个容量为256KB 的字库空间单位。字库文件的命名的编号从0~127，表示字库在IoTgus屏的存储位置：

| 字库编号 | 文件名称 | 占用字库个数 | 说明 |
| :--- | :--- | :--- | :--- |
| 0~11 | 0\_ASCII.HZK | 11 | 0号字库占用12个字库空间 |
| 12 | 12\_PYK.bin | 1 | 12号拼音库文件，中文输入 |
| 13 | 13触控配置文件.bin | 1 | 13号触控变量配置文件，通过配置工具生成 |
| 14~21 | 14变量配置文件.bin | 8 | 14号显示变量配置文件，通过配置工具生成 |
| 22 | 22\_Config.bin | 1 | 22号变量初始化文件，可通过配置工具生成 |
| 23 | 23\_OS.bin | 1 | 23号OS文件，通过编译工具生成 |
| 24-127 | 自定义字库和ico文件 | 103 | 自定义字库文件和图标库文件共用编号 |

## 配置文件说明

### 系统参数配置文件（CONFIG.txt）

系统参数配置文件（CONFIG.txt）采用类似脚本语言的方式来描述参数寄存器，每一行描述一个参数，不用的参数可以不写，具体如下表所示：

| 寄存器名称 | 取值范围 | 说明 |
| :--- | :--- | :--- |
| R0 | 出厂预设 | 用户不需要配置 |
| R1 | 0x00~0x12、0xFE | 波特率设置 |
| R2 | 0x00~0xFF | 设置系统工作模式1 |
| R3 | 0x00~0xFF | 帧头高字节 |
| R5 | 0x00~0xFF | 自定义波特率高字节 |
| R6 | 0x00~0xFF | 开启背光控制功能后，操作屏后背光亮度 |
| R7 | 0x00~0xFF | 开启背光控制功能后，一段时间无操作后的背光亮度 |
| R8 | 0x01~0xFF | 开启背光控制功能后，R7中的一段时间长度 |
| RA | 0x01~0xFF | 帧头低字节 |
| RB | 0x5A/0xDA | 格式化。0x5A高级格式化，0xDA低级格式化 |
| RC | 0x00~0xFF | 设置系统工作模式2 |
| RD | 0x7F/0xFF | 0x7F配置电容屏，0xFF配置为电阻屏 |

> config配置文件的参数均为一个字节的十六进制数，比如0C表示十进制的12；参数必须为2位，比如00不能写成0.

#### 液晶屏索引号寄存器（R0）

IoTgus屏支持的分辨率从320x240 到1024x768 等多种，通过设置R0 实现不同分辨率之间的切换。显示终端在出厂时，已经设置好了R0 参数，用户在使用过程中无须再次配置，如配置不当将导致显示异常。

| R0取值 | 对应分辨率 | 说明 |
| :--- | :--- | :--- |
| 20 | 320X240 | 3.5寸 |
| 21 | 480X272 | 4.3寸，天马微电子4.3寸液晶屏 |
| 22 | 480X272 | 4.3、5.0寸 |
| 01 | 640X480 | 5.6寸 |
| 02 | 800X 480 | 5、7寸 |
| 03 | 800X600 | 8寸 |
| 04 | 800X480 | 5寸 |
| 05 | 800X600 | 12.1，液晶屏自带背光控制模块 |
| 07 | 1024X768 | 15寸，BOE液晶屏 |
| 08 | 1024X768 | 15寸，LG液晶屏 |
| 09 | 1027X768 | 9.7寸 |
| 0A | 1024X600 | 7.0寸 |
| 0B | 1024X600 | 10.1寸 |
| 0C | 1024X768 | 15.0寸，液晶屏带背光控制模块 |

#### 波特率配置寄存器（R1、R5、R9）

波特率配置寄存器有固定和自定义波特率两种方式，用户可以依据需要自行设定串口通信波特率。 

| 寄存器名称 | 取值范围 | 说明 |
| :--- | :--- | :--- |
| R1 | 0x00~0x12，0xFE | 当取值为0xFE时，为自定义波特率 |
| R5 | 0x00~0xFF | 自定义波特率高字节 |
| R9 | 0x00~0xFF | 自定义波特率低字节 |

（1）当R1取值在0x00 至0x12之间  
每个值对应的串口通信速率是固定的速率，具体对应值如下表所示

| R1取值 | 波特率 |
| :--- | :--- |
| 00 | 1200 |
| 01 | 2400 |
| 02 | 4800 |
| 03 | 9600 |
| 04 | 19200 |
| 05 | 38400 |
| 06 | 57600 |
| 07 | 115200 |
| 08 | 28800 |
| 09 | 76800 |
| 0A | 62500 |
| 0B | 125000 |
| 0C | 250000 |
| 0D | 230400 |
| 0E | 345600 |
| 0F | 460800 |
| 10 | 625000 |
| 11 | 691200 |
| 12 | 921600 |

（2）当R1设置为0xFE  
用户自定义波特率，由R5和R9寄存器的值而定，波特率的计算方式：

> 波特率 = 6250000 ÷ \(R5 \* 256 + R6\)

如果R5 寄存器的 值为0，则R9 寄存器的取值必须大于0；如果R5 寄存器的取值大于0，则R9 寄存器的取值可以从0 开始；

（3）当R1设置为非0x00 ~ 0x12、0xFE  
串口通信速率默认为115200bps

#### 设置系统工作模式1（R2）

系统工作模式1的设置，对R1的不同位的配置，有不同的功能

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x4F4D;</th>
      <th style="text-align:left">&#x6743;&#x91CD;</th>
      <th style="text-align:left">&#x5B9A;&#x4E49;</th>
      <th style="text-align:left">&#x503C;</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">.7</td>
      <td style="text-align:left">0x80</td>
      <td style="text-align:left">VDS</td>
      <td style="text-align:left">0&#xFF1A;&#x6B63;&#x5E38;&#x663E;&#x793A;&#xFF0C;1&#xFF1A;&#x504F;&#x8F6C;90&#xB0;&#x663E;&#x793A;</td>
      <td
      style="text-align:left">&#x6B64;&#x529F;&#x80FD;&#x9700;&#x8981;&#x7279;&#x5B9A;&#x5185;&#x6838;</td>
    </tr>
    <tr>
      <td style="text-align:left">.6</td>
      <td style="text-align:left">0x40</td>
      <td style="text-align:left">&#x4FDD;&#x7559;</td>
      <td style="text-align:left">0</td>
      <td style="text-align:left">&#x7CFB;&#x7EDF;&#x4FDD;&#x7559;&#x4F4D;</td>
    </tr>
    <tr>
      <td style="text-align:left">.5</td>
      <td style="text-align:left">0x20</td>
      <td style="text-align:left">TPLED</td>
      <td style="text-align:left">0&#xFF1A;&#x7981;&#x6B62;&#x80CC;&#x5149;&#x63A7;&#x5236;&#xFF0C;1&#xFF1A;&#x542F;&#x52A8;&#x80CC;&#x5149;&#x63A7;&#x5236;</td>
      <td
      style="text-align:left">&#x53C2;&#x6570;&#x7531;R6&#x3001;R7&#x3001;R8&#x914D;&#x7F6E;</td>
    </tr>
    <tr>
      <td style="text-align:left">.4</td>
      <td style="text-align:left">0x10</td>
      <td style="text-align:left">FCRC</td>
      <td style="text-align:left">0&#xFF1A;&#x7981;&#x6B62;CRC16&#x6821;&#x9A8C;&#xFF0C;1&#xFF1A;&#x542F;&#x7528;CRC16&#x6821;&#x9A8C;</td>
      <td
      style="text-align:left">&#x6821;&#x9A8C;&#x4F7F;&#x80FD;&#x4F4D;</td>
    </tr>
    <tr>
      <td style="text-align:left">.3</td>
      <td style="text-align:left">0x08</td>
      <td style="text-align:left">TPSAUTO</td>
      <td style="text-align:left">
        <p>0&#xFF1A;&#x7981;&#x6B62;IoTgus&#x5C4F;&#x952E;&#x63A7;&#x6570;&#x636E;&#x81EA;&#x52A8;&#x4E0A;&#x4F20;</p>
        <p>1&#xFF1A;&#x5F00;&#x542F;IoTgus&#x5C4F;&#x952E;&#x63A7;&#x6570;&#x636E;&#x81EA;&#x52A8;&#x4E0A;&#x4F20;</p>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">.2</td>
      <td style="text-align:left">0x04</td>
      <td style="text-align:left">L22_InitEn</td>
      <td style="text-align:left">
        <p>0&#xFF1A;&#x5173;&#x95ED;IoTgus&#x5C4F;&#x4E0A;&#x7535;&#x521D;&#x59CB;&#x5316;&#x529F;&#x80FD;</p>
        <p>1&#xFF1A;&#x5F00;&#x542F;IoTgus&#x5C4F;&#x4E0A;&#x7535;&#x521D;&#x59CB;&#x5316;&#x529F;&#x80FD;</p>
      </td>
      <td style="text-align:left">IoTgus&#x53D8;&#x91CF;&#x521D;&#x59CB;&#x5316;&#x529F;&#x80FD;</td>
    </tr>
    <tr>
      <td style="text-align:left">.1</td>
      <td style="text-align:left">0x02</td>
      <td style="text-align:left">FRS1</td>
      <td style="text-align:left">&#x5237;&#x65B0;&#x5468;&#x671F;&#xFF0C;&#x9ED8;&#x8BA4;&#x4F7F;&#x7528;0</td>
      <td
      style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">.0</td>
      <td style="text-align:left">0x1</td>
      <td style="text-align:left">FRS0</td>
      <td style="text-align:left">&#x5237;&#x65B0;&#x5468;&#x671F;&#xFF0C;&#x9ED8;&#x8BA4;&#x4F7F;&#x7528;0</td>
      <td
      style="text-align:left"></td>
    </tr>
  </tbody>
</table>

#### 通信帧帧头寄存器（R3、RA）

IoTgus屏中的通信帧结构由帧头、长度、指令、数据、校验，5个部分组成，其中帧头是有R3和RA组成，显示终端的串口通信帧头信息出厂时默认为0x5AA5，即R3 为5A、RA 为A5。

| 寄存器名称 | 取值范围 | 说明 |
| :--- | :--- | :--- |
| R3 | 0x00~0xFF | 帧头高字节 |
| RA | 0x00~0xFF | 帧头低字节 |

通信数据帧的帧头信息的作用有：

1. 方便显示串口通信系统中的各个终端识别通信信道中的数据，避免数据不正常时引起显示终端异常；
2. 当多个系统或者终端并联工作时，帧头可以作为各设备的识别地址，避免因通信引起干扰问题。

#### 屏保功能寄存器（R6、R7、R8）

当R2的第5位置位1时，背光将受IoTgus屏操作控制（背光待机后，第一次触控操作不会触发动作）。

| 寄存器名称 | 取值范围 | 示例值 | 说明 |
| :--- | :--- | :--- | :--- |
| R6 | 0x00~0x3F | 0x3F | 开启背光控制功能后，操作屏后背光亮度 |
| R7 | 0x00~0x3F | 0x10 | 开启背光控制功能后，一段时间无操作后的背光亮度 |
| R8 | 0x01~0xFF | 0x1E | 开启背光控制功能后，R7中的一段时间长度 |

> 示例：当R2的第5位置位1时，且R6 为0x3F，R7 为0x10，R8 为1E，30 秒不点击触摸屏，背光亮度将自动降低到0x10； 点击触摸屏后，背光亮度动调节到0x3F。

#### 设置系统工作模式2（RC）

系统工作模式2的设置，对R2的不同位的配置，有不同的功能

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x4F4D;</th>
      <th style="text-align:left">&#x6743;&#x91CD;</th>
      <th style="text-align:left">&#x5B9A;&#x4E49;</th>
      <th style="text-align:left">&#x503C;</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">.7</td>
      <td style="text-align:left">0x80</td>
      <td style="text-align:left">&#x4FDD;&#x7559;</td>
      <td style="text-align:left">0</td>
      <td style="text-align:left">&#x5199;0</td>
    </tr>
    <tr>
      <td style="text-align:left">.6</td>
      <td style="text-align:left">0x40</td>
      <td style="text-align:left">OSEnable</td>
      <td style="text-align:left">0&#xFF1A;&#x5173;&#x95ED;OS&#xFF0C;1&#xFF1A;&#x5F00;&#x542F;OS</td>
      <td
      style="text-align:left">&#x7CFB;&#x7EDF;&#x4FDD;&#x7559;&#x4F4D;</td>
    </tr>
    <tr>
      <td style="text-align:left">.5</td>
      <td style="text-align:left">0x20</td>
      <td style="text-align:left">TpBuzzEnable</td>
      <td style="text-align:left">0&#xFF1A;&#x5173;&#x95ED;&#x5C4F;&#x8702;&#x9E23;&#x5668;&#x58F0;&#x97F3;&#xFF0C;1&#xFF1A;&#x5173;&#x95ED;&#x5C4F;&#x8702;&#x9E23;&#x5668;&#x58F0;&#x97F3;</td>
      <td
      style="text-align:left">&#x53C2;&#x6570;&#x7531;R6&#x3001;R7&#x3001;R8&#x914D;&#x7F6E;</td>
    </tr>
    <tr>
      <td style="text-align:left">.4</td>
      <td style="text-align:left">0x10</td>
      <td style="text-align:left">page128enable</td>
      <td style="text-align:left">0&#xFF1A;&#x6BCF;&#x9875;&#x6700;&#x5927;&#x53EF;&#x914D;&#x7F6E;&#x663E;&#x793A;&#x53D8;&#x91CF;&#x63A7;&#x4EF6;64&#x4E2A;
        <br
        />1&#xFF1A;&#x6BCF;&#x6708;&#x6700;&#x5927;&#x53EF;&#x914D;&#x7F6E;&#x663E;&#x793A;&#x53D8;&#x91CF;&#x63A7;&#x4EF6;128&#x5206;</td>
      <td
      style="text-align:left">&#x53D8;&#x91CF;&#x914D;&#x7F6E;</td>
    </tr>
    <tr>
      <td style="text-align:left">.3</td>
      <td style="text-align:left">0x08</td>
      <td style="text-align:left">CRCAckEnable</td>
      <td style="text-align:left">
        <p>0&#xFF1A;&#x7981;&#x6B62;IoTgus&#x5C4F;&#x952E;&#x63A7;&#x6570;&#x636E;&#x81EA;&#x52A8;&#x4E0A;&#x4F20;</p>
        <p>1&#xFF1A;&#x5F00;&#x542F;IoTgus&#x5C4F;&#x952E;&#x63A7;&#x6570;&#x636E;&#x81EA;&#x52A8;&#x4E0A;&#x4F20;</p>
      </td>
      <td style="text-align:left">&#x952E;&#x63A7;&#x81EA;&#x52A8;&#x4E0A;&#x62A5;&#x6570;&#x636E;</td>
    </tr>
    <tr>
      <td style="text-align:left">.2</td>
      <td style="text-align:left">0x04</td>
      <td style="text-align:left">&#x4FDD;&#x7559;</td>
      <td style="text-align:left">&#x5199;0</td>
      <td style="text-align:left">&#x9884;&#x7559;</td>
    </tr>
    <tr>
      <td style="text-align:left">.1</td>
      <td style="text-align:left">0x02</td>
      <td style="text-align:left">&#x4FDD;&#x7559;</td>
      <td style="text-align:left">&#x5199;0</td>
      <td style="text-align:left">&#x9884;&#x7559;</td>
    </tr>
    <tr>
      <td style="text-align:left">.0</td>
      <td style="text-align:left">0x01</td>
      <td style="text-align:left">&#x4FDD;&#x7559;</td>
      <td style="text-align:left">&#x5199;0</td>
      <td style="text-align:left">&#x9884;&#x7559;</td>
    </tr>
  </tbody>
</table>

#### 触摸屏类型配置寄存器（RD）

IoTgus屏支持电阻和电容式触摸屏，用户根据需要选配，也可以选择不带触摸屏的终端。在出厂时，每个终端根据选配的触摸屏类型已经配置了RD参数，用户在可以不需要再次进行触摸屏类型进行配置。

### 数据转发规则文件（iotcfg.txt）

文件在物联网平台生成并导出。

