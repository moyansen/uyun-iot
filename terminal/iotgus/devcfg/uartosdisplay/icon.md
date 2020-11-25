# 图标显示功能

## 变量图标显示【0x00】

![&#x53D8;&#x91CF;&#x56FE;&#x6807;&#x663E;&#x793A;](../../../../.gitbook/assets/bian-liang-tu-biao-xian-shi-.png)

## 动画图标显示【0x01】

![&#x52A8;&#x753B;&#x56FE;&#x6807;](../../../../.gitbook/assets/dong-hua-tu-biao-.png)

> Tips： VP +1 为保留位，不可以他用 当变量不等于VStop 或者VStart 时，不显示图标或者动画

## 滑块刻度指示【0x02】

![&#x6ED1;&#x52A8;&#x523B;&#x5EA6;](../../../../.gitbook/assets/hua-dong-ke-du-xian-shi-.png)

## 艺术字变量显示【0x03】

![&#x827A;&#x672F;&#x5B57;&#x53D8;&#x91CF;](../../../../.gitbook/assets/yi-shu-zi-xian-shi-.png)

## 图片动画显示【0x04

![](../../../../.gitbook/assets/tu-pian-dong-hua-.png)

> Tips：起始图片索引号必须小于终止图片索引号；如果在终止页面也设置了图片动画变量，可以实现图片循环 显示；在图片动画过程中，可以通过0x80 指令或者触控指令切换页面，从而结束图片动画。

## 图标旋转指示【0x05】

![&#x56FE;&#x6807;&#x65CB;&#x8F6C;](../../../../.gitbook/assets/tu-biao-xuan-zhuan-.png)

> Tips：本指令主要用于仪表刻度盘的指针指示；旋转时始终假定为“顺时针”转动，即ALEnd 必须大于ALBegain。

![](../../../../.gitbook/assets/image%20%28150%29.png)

## 位变量图标显示【0x06】

![&#x4F4D;&#x53D8;&#x91CF;&#x56FE;&#x6807;](../../../../.gitbook/assets/wei-bian-liang-tu-biao-.png)

## 表盘时钟

![&#x8868;&#x76D8;&#x65F6;&#x949F;](../../../../.gitbook/assets/biao-pan-shi-zhong-.png)

