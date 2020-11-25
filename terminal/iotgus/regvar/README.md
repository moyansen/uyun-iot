# 寄存器说明

## 寄存器空间

寄存器空间容量为 256 Byte，用于硬件操作和图片显示等进程控制。寄存器与存储器不同，它是用来存放寄存器状态的，比如 RTC（实时时间）、背光亮度等实时的状态。通过0x80/0x81指令改变各寄存器的值，可实现上位机与 IoTgus屏信息传 输及控制。寄存器详细定义如下：

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>&#x5BC4;&#x5B58;&#x5668;&#x5730;&#x5740;</b>
      </th>
      <th style="text-align:left"><b>R/W</b>
      </th>
      <th style="text-align:left"><b>&#x957F;&#x5EA6;(Byte)</b>
      </th>
      <th style="text-align:left"><b>&#x8BF4;&#x660E;</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">0x00</td>
      <td style="text-align:left">R</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">&#x7EC8;&#x7AEF;&#x7248;&#x672C;&#x53F7;&#xFF0C;BCD&#x7801;</td>
    </tr>
    <tr>
      <td style="text-align:left">0x01</td>
      <td style="text-align:left">R/W</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">LCD&#x80CC;&#x5149;&#x4EAE;&#x5EA6;&#xFF0C;0x00 ~ 0x3F</td>
    </tr>
    <tr>
      <td style="text-align:left">0x02</td>
      <td style="text-align:left">W</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">&#x8702;&#x9E23;&#x5668;&#x9E23;&#x53EB;&#x63A7;&#x5236;&#x5BC4;&#x5B58;&#x5668;&#xFF0C;&#x5355;&#x4F4D;&#x4E3A;10ms</td>
    </tr>
    <tr>
      <td style="text-align:left">0x03</td>
      <td style="text-align:left">R/W</td>
      <td style="text-align:left">2</td>
      <td style="text-align:left">&#x8BFB;&#xFF1A;&#x5F53;&#x524D;&#x663E;&#x793A;&#x9875;&#x9762;&#x7D22;&#x5F15;&#x53F7;</td>
    </tr>
    <tr>
      <td style="text-align:left">0x05</td>
      <td style="text-align:left">R/W</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">
        <p>&#x7528;&#x6237;&#x8BFB;&#x53D6;&#x6570;&#x636E;&#x540E;&#x672A;&#x6E05;&#x96F6;&#x672C;&#x6807;&#x8BB0;&#xFF0C;&#x5219;&#x89E6;&#x6478;&#x5750;&#x6807;&#x4E0D;&#x518D;&#x66F4;&#x65B0;</p>
        <p>0x5A&#xFF1A;&#x89E6;&#x6478;&#x5750;&#x6807;&#x6709;&#x66F4;&#x65B0;</p>
        <p>&#x5176;&#x4ED6;&#xFF1A;&#x89E6;&#x6478;&#x5750;&#x6807;&#x672A;&#x66F4;&#x65B0;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">0x06</td>
      <td style="text-align:left">R</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">
        <p>0x01&#xFF1A;&#x89E6;&#x6478;&#x5C4F;&#x9996;&#x6B21;&#x6309;&#x4E0B;</p>
        <p>0x02&#xFF1A;&#x89E6;&#x6478;&#x5C4F;&#x6309;&#x538B;&#x7ED3;&#x675F;</p>
        <p>0x03&#xFF1A;&#x4E00;&#x76F4;&#x6309;&#x538B;&#x4E2D;</p>
        <p>&#x5176;&#x4ED6;&#xFF1A;&#x65E0;&#x6548;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">0x07</td>
      <td style="text-align:left">R</td>
      <td style="text-align:left">4</td>
      <td style="text-align:left">&#x89E6;&#x6478;&#x6309;&#x538B;&#x5750;&#x6807;&#x4F4D;&#x7F6E;&#xFF1A;Xh
        Xl Yh Yl</td>
    </tr>
    <tr>
      <td style="text-align:left">0x0B</td>
      <td style="text-align:left">R/W</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">
        <p>0x00&#xFF1A;&#x7981;&#x6B62;&#x89E6;&#x63A7;&#x529F;&#x80FD;</p>
        <p>&#x5176;&#x4ED6;&#xFF1A;&#x4F7F;&#x80FD;&#x89E6;&#x63A7;&#x529F;&#x80FD;
          <br
          />&#x4E0A;&#x7535;&#x9ED8;&#x8BA4;&#x4E3A;0xFF</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">0x0C</td>
      <td style="text-align:left">R</td>
      <td style="text-align:left">4</td>
      <td style="text-align:left">
        <p>&#x4E0A;&#x7535;&#x8FD0;&#x884C;&#x65F6;&#x95F4;&#xFF0C;BCD&#x7801;&#xFF0C;&#x683C;&#x5F0F;&#xFF1A;&#x65F6;&#xFF1A;&#x5206;&#xFF1A;&#x79D2;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;9999:59:59</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">0x10</td>
      <td style="text-align:left">R</td>
      <td style="text-align:left">13</td>
      <td style="text-align:left">TF&#x5361;&#x914D;&#x7F6E;&#x5BC4;&#x5B58;&#x5668;&#x7684;&#x6620;&#x5C04;</td>
    </tr>
    <tr>
      <td style="text-align:left">0x1D</td>
      <td style="text-align:left">W</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">&#x91CD;&#x8BBE;R1 ~ RC&#x5BC4;&#x5B58;&#x5668;&#x6807;&#x5FD7;</td>
    </tr>
    <tr>
      <td style="text-align:left">0x1E</td>
      <td style="text-align:left">R</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">&#x5F53;&#x524D;&#x80CC;&#x5149;&#x4EAE;&#x5EA6;&#x503C;</td>
    </tr>
    <tr>
      <td style="text-align:left">0x1F</td>
      <td style="text-align:left">W</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">0x5A&#x8868;&#x793A;&#x91CD;&#x65B0;&#x8BBE;&#x7F6E;&#x65F6;&#x949F;&#xFF0C;&#x7EC8;&#x7AEF;&#x6267;&#x884C;&#x540E;&#x6E05;&#x96F6;</td>
    </tr>
    <tr>
      <td style="text-align:left">0x20</td>
      <td style="text-align:left">R/W</td>
      <td style="text-align:left">7</td>
      <td style="text-align:left">YY:MM:DD:WW:HH:MM:SS</td>
    </tr>
    <tr>
      <td style="text-align:left">0x27</td>
      <td style="text-align:left">&#x2014;</td>
      <td style="text-align:left">25</td>
      <td style="text-align:left">&#x4FDD;&#x7559;</td>
    </tr>
    <tr>
      <td style="text-align:left">0x40</td>
      <td style="text-align:left">R/W</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">0x5A&#x8868;&#x793A;&#x4F7F;&#x80FD;&#x5B57;&#x5E93;&#x5B58;&#x50A8;&#x5355;&#x5143;&#x64CD;&#x4F5C;&#xFF0C;&#x7EC8;&#x7AEF;&#x6267;&#x884C;&#x540E;&#x6E05;&#x96F6;</td>
    </tr>
    <tr>
      <td style="text-align:left">0x41</td>
      <td style="text-align:left">W</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">0xA0&#xFF1A;&#x5C06;&#x5236;&#x5B9A;&#x5B57;&#x5E93;&#x7A7A;&#x95F4;&#x7684;&#x6570;&#x636E;&#x5199;&#x5230;&#x53D8;&#x91CF;&#x5B58;&#x50A8;&#x7A7A;&#x95F4;</td>
    </tr>
    <tr>
      <td style="text-align:left">0x42</td>
      <td style="text-align:left">W</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">&#x5B57;&#x5E93;&#x7D22;&#x5F15;&#x53F7;&#xFF0C;&#x8303;&#x56F4;0x40 ~
        0x7F</td>
    </tr>
    <tr>
      <td style="text-align:left">0x43</td>
      <td style="text-align:left">W</td>
      <td style="text-align:left">3</td>
      <td style="text-align:left">&#x9884;&#x8BFB;&#x53D6;&#x5B57;&#x5E93;&#x7A7A;&#x95F4;&#x7684;&#x9996;&#x5730;&#x5740;&#xFF0C;&#x8303;&#x56F4;0x000000
        ~ 0x01FFFF</td>
    </tr>
    <tr>
      <td style="text-align:left">0x46</td>
      <td style="text-align:left">W</td>
      <td style="text-align:left">2</td>
      <td style="text-align:left">&#x9884;&#x5199;&#x5165;&#x53D8;&#x91CF;&#x7A7A;&#x95F4;&#x7684;&#x9996;&#x5730;&#x5740;&#xFF0C;&#x8303;&#x56F4;0x0000
        ~ 0x6FFF</td>
    </tr>
    <tr>
      <td style="text-align:left">0x48</td>
      <td style="text-align:left">W</td>
      <td style="text-align:left">2</td>
      <td style="text-align:left">&#x9884;&#x8BFB;&#x53D6;&#x7684;&#x6570;&#x636E;&#x957F;&#x5EA6;&#xFF0C;&#x8303;&#x56F4;0x0001
        ~ 0x6FFF</td>
    </tr>
    <tr>
      <td style="text-align:left">0x4A</td>
      <td style="text-align:left">R/W</td>
      <td style="text-align:left">2</td>
      <td style="text-align:left">&#x8F6F;&#x4EF6;&#x5B9A;&#x65F6;&#x5668;0</td>
    </tr>
    <tr>
      <td style="text-align:left">0x4C</td>
      <td style="text-align:left">R/W</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">&#x8F6F;&#x4EF6;&#x5B9A;&#x65F6;&#x5668;1</td>
    </tr>
    <tr>
      <td style="text-align:left">0x4D</td>
      <td style="text-align:left">R/W</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">&#x8F6F;&#x4EF6;&#x5B9A;&#x65F6;&#x5668;2</td>
    </tr>
    <tr>
      <td style="text-align:left">0x4E</td>
      <td style="text-align:left">R/W</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">&#x8F6F;&#x4EF6;&#x5B9A;&#x65F6;&#x5668;3</td>
    </tr>
    <tr>
      <td style="text-align:left">0x4F</td>
      <td style="text-align:left">W</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">&#x89E6;&#x63A7;&#x952E;&#x7801;&#xFF0C;&#x7528;&#x4E8E;&#x51FA;&#x53D1;13&#x89E6;&#x63A7;&#x6587;&#x4EF6;&#xFF1B;&#x6709;&#x6548;&#x503C;&#xFF1A;0x01
        ~ 0xFF&#xFF1B;0x00&#x8868;&#x793A;&#x65E0;&#x6548;&#xFF1B;&#x7EC8;&#x7AEF;&#x5904;&#x7406;&#x952E;&#x7801;&#x4E4B;&#x540E;&#x4F1A;&#x81EA;&#x52A8;&#x6E05;&#x96F6;&#x952E;&#x7801;&#x5BC4;&#x5B58;&#x5668;</td>
    </tr>
    <tr>
      <td style="text-align:left">0x50</td>
      <td style="text-align:left">W</td>
      <td style="text-align:left">3</td>
      <td style="text-align:left">
        <p>&#x64AD;&#x653E;&#x9884;&#x7F6E;&#x7684;&#x97F3;&#x9891;&#x6587;&#x4EF6;&#xFF1B;&#x683C;&#x5F0F;&#xFF1A;0x5A
          PlayStartID PlayNum</p>
        <p>0x5A&#xFF1A;&#x4F7F;&#x80FD;&#x97F3;&#x9891;&#x64AD;&#x653E;&#x529F;&#x80FD;</p>
        <p>PlayStartID&#xFF1A;&#x64AD;&#x653E;&#x97F3;&#x9891;&#x6587;&#x4EF6;&#x5F00;&#x59CB;&#x6BB5;&#x7D22;&#x5F15;&#x53F7;</p>
        <p>PlayNum&#xFF1A;&#x64AD;&#x653E;&#x97F3;&#x9891;&#x6587;&#x4EF6;&#x7684;&#x6BB5;&#x6570;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">0x53</td>
      <td style="text-align:left">W</td>
      <td style="text-align:left">2</td>
      <td style="text-align:left">
        <p>&#x8C03;&#x6574;&#x97F3;&#x9891;&#x64AD;&#x653E;&#x7684;&#x97F3;&#x91CF;&#xFF1B;&#x683C;&#x5F0F;&#xFF1A;0x5A
          VOL</p>
        <p>0x5A&#xFF1A;&#x4F7F;&#x80FD;&#x97F3;&#x9891;&#x64AD;&#x653E;&#x97F3;&#x91CF;&#x8C03;&#x6574;&#x529F;&#x80FD;</p>
        <p>VOL&#xFF1A;&#x9884;&#x8C03;&#x6574;&#x7684;&#x97F3;&#x91CF;&#x6570;&#x503C;&#xFF1B;&#x97F3;&#x91CF;&#x4E3A;VOL/64&#xFF0C;&#x9ED8;&#x8BA4;&#x503C;&#x662F;64&#x3002;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">0x55</td>
      <td style="text-align:left">&#x2014;</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">&#x4FDD;&#x7559;</td>
    </tr>
    <tr>
      <td style="text-align:left">0x56</td>
      <td style="text-align:left">R/W</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">0x5A&#x8868;&#x793A;&#x4F7F;&#x80FD;&#x5B57;&#x5E93;&#x5B58;&#x50A8;&#x5355;&#x5143;&#x64CD;&#x4F5C;&#xFF0C;&#x7EC8;&#x7AEF;&#x6267;&#x884C;&#x540E;&#x6E05;&#x96F6;</td>
    </tr>
    <tr>
      <td style="text-align:left">0x57</td>
      <td style="text-align:left">W</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">
        <p>0x50&#xFF1A;&#x5C06;&#x53D8;&#x91CF;&#x5B58;&#x50A8;&#x7A7A;&#x95F4;&#x7684;&#x6570;&#x636E;&#x5199;&#x5165;&#x6570;&#x636E;&#x5B58;&#x50A8;&#x7A7A;&#x95F4;</p>
        <p>0xA0&#xFF1A;&#x5C06;&#x6570;&#x636E;&#x5B58;&#x50A8;&#x7A7A;&#x95F4;&#x7684;&#x6570;&#x636E;&#x8BFB;&#x53D6;&#x5230;&#x53D8;&#x91CF;&#x5B58;&#x50A8;&#x7A7A;&#x95F4;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">0x58</td>
      <td style="text-align:left">W</td>
      <td style="text-align:left">4</td>
      <td style="text-align:left">&#x6570;&#x636E;&#x5E93;&#x7A7A;&#x95F4;&#x5B57;&#x5730;&#x5740;&#xFF0C;0x00000000
        ~ 0x01C1FFFF&#xFF0C;&#x6700;&#x5927;450MW&#xFF08;900MB&#xFF0C;&#x53D6;&#x51B3;&#x4E8E;&#x5185;&#x6838;
        Flash &#x60C5;&#x51B5;&#xFF09;&#x6570;&#x636E;&#x5E93;&#x7A7A;&#x95F4;&#x3002;&#x6570;&#x636E;&#x5E93;&#x4ECE;&#x7269;&#x7406;&#x5B58;&#x50A8;&#x7A7A;&#x95F4;&#x7684;&#x7B2C;64MB&#x5F00;&#x59CB;&#x5B58;&#x50A8;&#xFF0C;&#x4E0E;&#x56FE;&#x7247;&#x5B58;&#x50A8;&#x5668;&#x7A7A;&#x95F4;&#x6709;&#x91CD;&#x5408;&#xFF0C;&#x6BCF;&#x4E2A;&#x6570;&#x636E;&#x5B58;&#x50A8;&#x5668;&#x5360;&#x636E;2Byte&#x7269;&#x7406;&#x5B58;&#x50A8;&#x5668;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">0x5C</td>
      <td style="text-align:left">W</td>
      <td style="text-align:left">2</td>
      <td style="text-align:left">&#x6307;&#x5B9A;&#x53D8;&#x91CF;&#x5B58;&#x50A8;&#x5668;&#x7A7A;&#x95F4;&#x7684;&#x6570;&#x636E;&#x5E93;&#x64CD;&#x4F5C;&#x9996;&#xFF08;&#x5B57;&#xFF09;&#x5730;&#x5740;&#xFF0C;&#x8303;&#x56F4;0x0000
        ~ 0x6FFF</td>
    </tr>
    <tr>
      <td style="text-align:left">0x5E</td>
      <td style="text-align:left">W</td>
      <td style="text-align:left">2</td>
      <td style="text-align:left">&#x9884;&#x8BFB;&#x53D6;&#x7684;&#x6570;&#x636E;&#x957F;&#x5EA6;&#xFF0C;&#x8303;&#x56F4;0x0001
        ~ 0x6FFF</td>
    </tr>
    <tr>
      <td style="text-align:left">0x60</td>
      <td style="text-align:left">&#x2014;</td>
      <td style="text-align:left">139</td>
      <td style="text-align:left">&#x4FDD;&#x7559;</td>
    </tr>
    <tr>
      <td style="text-align:left">0xEA</td>
      <td style="text-align:left">W</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">&#x5199;&#x5165;0x5A&#x4F7F;&#x80FD;&#x89E6;&#x6478;&#x5C4F;&#x6821;&#x51C6;&#xFF0C;&#x6821;&#x51C6;&#x5B8C;&#x6210;&#x540E;&#x81EA;&#x52A8;&#x6E05;&#x96F6;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">0xEB</td>
      <td style="text-align:left">W</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">
        <p>&#x5199;&#x5165;&#x7279;&#x6B8A;&#x5B9A;&#x4E49;&#x7684;&#x6570;&#x503C;&#x4EE5;&#x6E05;&#x9664;&#x5BF9;&#x5E94;&#x7684;&#x66F2;&#x7EBF;&#x7F13;&#x51B2;&#x533A;&#x6570;&#x636E;&#x3002;</p>
        <p>0x55&#xFF1A;&#x6E05;&#x9664;&#x5168;&#x90E8; 8 &#x6761;&#x66F2;&#x7EBF;&#x7F13;&#x51B2;&#x533A;&#x6570;&#x636E;</p>
        <p>0x56 ~ 0x5D&#xFF1A;&#x5206;&#x522B;&#x6E05;&#x9664; CH0-CH7 &#x901A;&#x9053;&#x7684;&#x66F2;&#x7EBF;&#x7F13;&#x51B2;&#x533A;&#x6570;&#x636E;</p>
        <p>&#x66F2;&#x7EBF;&#x7F13;&#x51B2;&#x533A;&#x6570;&#x636E;&#x6E05;&#x9664;&#x540E;&#xFF0C;&#x672C;&#x5BC4;&#x5B58;&#x5668;&#x4F1A;&#x88AB;&#x7EC8;&#x7AEF;&#x6E05;&#x96F6;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">0xEC</td>
      <td style="text-align:left">&#x2014;</td>
      <td style="text-align:left">2</td>
      <td style="text-align:left">&#x4FDD;&#x7559;</td>
    </tr>
    <tr>
      <td style="text-align:left">0xEE</td>
      <td style="text-align:left">W</td>
      <td style="text-align:left">2</td>
      <td style="text-align:left">&#x5199;&#x5165;0x5AA5&#xFF0C;&#x4F7F;&#x80FD;&#x4E00;&#x6B21;&#x7CFB;&#x7EDF;&#x590D;&#x4F4D;&#x529F;&#x80FD;</td>
    </tr>
    <tr>
      <td style="text-align:left">0xF0</td>
      <td style="text-align:left">&#x2014;</td>
      <td style="text-align:left">16</td>
      <td style="text-align:left">&#x4FDD;&#x7559;</td>
    </tr>
  </tbody>
</table>

## 变量空

IoTgus显示终端与控制板或者上位的数据交互是基于变量地址的。变量空间固定为65KB，分割为地址 0x0000~0xFFFF 的子变量空间。每一个变量地址对应的空间占 2 字节。在 IoTgus 中使用变量地址或描述指针时，设置的变量地址为数据储存空间的起始地址，即数据从设置的地址（起始地址）开始按序依次储存。每个起始变量地址都指向的空间大小是不固定的，因此在配置工具中给各个变量分配变量地址时，分配好变量空间，否则将可能出现分配空间的重叠而导致显示错误。

变量空间中的0x8000~0xFFFF分配用于网络功能配置使用，用户在进行数据交互是，如果使用IoT功能，应当避开，以免造成冲突。



