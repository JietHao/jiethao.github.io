# C语言

> [C语言中文网](http://c.biancheng.net/c/)

> 不学C语言是码农，学了C语言是程序员。

## 编程基础

* 编程语言是用来控制计算机的一系列指令（Instruction），它有固定的格式和词汇（不同编程语言的格式和词汇不一样），必须遵守，否则就会出错，达不到我们的目的。
* C语言概念少，词汇少，包含了基本的编程元素，后来的很多语言（C++、Java等）都参考了C语言，说C语言是现代编程语言的开山鼻祖毫不夸张，它改变了编程世界。
* 从C语言到内存，从内存到进程和线程，环环相扣：不学C语言就吃不透内存，不学内存就吃不透进程和线程。

* 数制及转换：二进制、八进制、十进制、十六进制
* 二进制存储
  * 1个元器件称为1比特（Bit）或1位，8个元器件称为1字节（Byte）。
  * 单位换算
    ```
    1Byte = 8 Bit
    1KB = 1024Byte = 210Byte
    1MB = 1024KB = 220Byte
    1GB = 1024MB = 230Byte
    1TB = 1024GB = 240Byte
    1PB = 1024TB = 250Byte
    1EB = 1024PB = 260Byte
    ```

* 1.12 载入内存
  * 载入内存（Load into Memory）
  * 加载器（Loader）
  * 虚拟内存
    * 硬盘中就会有一部分空间用来存放内存中暂时不用的数据。这一部分空间就叫做虚拟内存（Virtual Memory）。

* 1.13 字符编码
  * 特定的文字必然对应着固定的二进制，否则在转换时将发生混乱。
  * 怎样将文字与二进制对应起来呢？这就需要有一套规范，计算机公司和软件开发者都必须遵守。
  * 这样的一套规范就称为字符集（Character Set）或者字符编码（Character Encoding）。
  * 拉丁字母、阿拉伯字母、斯拉夫字母（西里尔字母）被称为世界三大字母体系。
  * ASCII 是"American Standard Code for Information Interchange"的缩写，翻译过来是"美国信息交换标准代码"

* 1.17 [不要这样学习C语言，这是一个坑！](https://www.cnblogs.com/zhangjinfu/articles/11270080.html)

## C语言初探



## 记录
1. 不支持嵌套定义
2. 形参 VS 实参 (http://c.biancheng.net/view/1853.html)




C Library (http://www.cplusplus.com/reference/clibrary/)
```
合格程序员：<stdio.h>、<ctype.h>、<stdlib.h>、<string.h>
熟练程序员：<assert.h>、<limits.h>、<stddef.h>、<time.h>
优秀程序员：<float.h>、<math.h>、<error.h>、<locale.h>、<setjmp.h>、<signal.h>、<stdarg.h>
```