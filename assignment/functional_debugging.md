# LAB11实验报告
## 实验任务
### 熟悉KEIL调试器的使用
### 运行代码，观察Register和Memory的值的变化
### 找出Cnt变量的最终值和HappyBuf的最终值，并截图，给出该截图，并解释如何得到结论。

## 程序简介
### 有2个缓冲区HappyBuf和SadBuf，程序将happy和sad两个8位变量赋为随机数，再将这两个变量转存到数组中，Cnt保存数组偏移量，Cnt被初始化为0，转存时先判断Cnt是否越界，若否，则将变量转存再将Cnt加1。

## 结果截图
![enter description here][2]

## 结论解释
### 程序首先将Cnt的值初始化为0。
![enter description here][3]
### 在Random函数中生成一个0到2^32-1之间的一个随机数，并储存在R0中。
![enter description here][4]
### 将R0取低8位赋值给happy和sad。
![enter description here][5]
### 此时比较Cnt和Size的值，相等时表示数组已经存满了，不相等则Cnt加1，继续循环。
![enter description here][6]
### 综上，程序中将Size的值设置为20，每次将Cnt和Size做cmp运算来判断是否越界，因此最后Cnt的值为0x00000014，HappyBuf中存放每一次循环中happy的随机值。


  [1]: ./images/keil%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BE.jpg "keil实验截图.jpg"
  [2]: ./images/keil%E5%AE%9E%E9%AA%8C%E6%88%AA%E5%9B%BE2.jpg "keil实验截图2.jpg"
  [3]: ./images/step1.jpg "step1.jpg"
  [4]: ./images/step2.jpg "step2.jpg"
  [5]: ./images/step3.jpg "step3.jpg"
  [6]: ./images/step4.jpg "step4.jpg"
