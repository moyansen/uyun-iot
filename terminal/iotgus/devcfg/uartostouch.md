# 触控控件说明

## 1、数据录入【0xFE00/0xFD00】

![](../../../.gitbook/assets/image%20%2899%29.png)

![](../../../.gitbook/assets/image%20%2877%29.png)

> Tips：输入过程中有效键码为0x0030\(0\) ~ 0x0039\(9\)、0x002E\(.\)、0x00F0\(cancel\)、0x00F1（enter）、0x00F2\(BackSpace\)。

## 2、菜单操作【0xFE01/0xFD01】

![](../../../.gitbook/assets/image%20%2898%29.png)

> Tips：输入过程中有效键码：0x0000 ~ 0x00FF，其中0x00FF 为取消（不选择参数直接返回）。

## 3、增量调节【0xFE02/0xFD02】

![](../../../.gitbook/assets/image%20%28162%29.png)

## 4、拖动调节【0xFE03/0xFD03】

![](../../../.gitbook/assets/image%20%2854%29.png)

## 5、时钟调整【0xFE04/0xFD04】

![](../../../.gitbook/assets/image%20%2882%29.png)

## 6、按键值返回【0xFE05/0xFD05】

![](../../../.gitbook/assets/image%20%28134%29.png)

## 7、文本录入【0xFE06/0xFD06】

在文本录入的触控文件中，两字节键码的低字节表示普通键码，高字节表示大写键码。典型的文本录入键盘定 义如下表所示：

![](../../../.gitbook/assets/image%20%2889%29.png)

> Tips：文本键盘键码须小于0x80（ASCII 码）。0x0D 键码录入会自动转换成0x0D 0x0A；0x00 和0xFF 键码禁用。

特殊功能键盘键码定义

![](../../../.gitbook/assets/image%20%2860%29.png)

使用键盘（0x4F 寄存器保存的键码）做文本录入时，如果使用CapsLock 键，请把按钮的动画区域定义在需要 提示“CapsLock”的区域；这样定义后，发送CapsLock 键时，屏幕的相应位置会自动显示“CapsLock”的区域图 标提示。

### 7.1、ASCII 录入

![](../../../.gitbook/assets/image%20%28106%29.png)

![](../../../.gitbook/assets/image%20%287%29.png)

> Tips：显示终端预装0 号字库包含4\*8 ~ 64\*128 点阵的所有ASCII字模

### 7.2、GBK 录入

![](../../../.gitbook/assets/image%20%28144%29.png)

![](../../../.gitbook/assets/image%20%2842%29.png)

![](../../../.gitbook/assets/image%20%283%29.png)

> Tips：
>
> 拼音“bd”对应所有GBK 编码的全角标点符号录入
>
> AG 系列智能显示终端出厂时均预装了0 号ASCII 字库，内含4_8 ~ 64_128 点阵的所有ASCII 字符

## 8、触控同步数据返回【0xFE08/0xFD08】

![](../../../.gitbook/assets/image%20%2868%29.png)

![](../../../.gitbook/assets/image%20%28152%29.png)

![](../../../.gitbook/assets/image%20%2812%29.png)

触摸屏按压的三种状态如下图所示：

![](../../../.gitbook/assets/image%20%28124%29.png)





