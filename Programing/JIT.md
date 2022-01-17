# JIT

## 概念
1. 动态编译（dynamic compilation），指”在运行时进行编译”
   - JIT编译（just-in-time compilation），当代码第一次被执行时进行编译，动态编译的一种特例。
   - 自适应动态编译（adpative dynamic compilation），执行时机比JIT编译迟，先让程序以“某种方式”先运行起来，收集一些信息后再做动态编译。
2. 事前编译（ahead-of-time compilation），指“在运行前进行编译”，也叫静态编译（static compilation）


## 虚拟机架构：解释器和编译器并存
- 解释器执行：输入的代码 -> [ 解释器 解释执行 ] -> 执行结果
- JIT编译执行：输入的代码 -> [ 编译器 编译 ] -> 编译后的代码 -> [ 执行 ] -> 执行结果

- “只执行一次”，解释器比JIT编译执行快，如：
  - 只被调用一次
  - 没有循环
- 频繁执行的代码，JIT编译执行更快。

- 编译开销：代码膨胀，“代码爆炸”
- 只对需要编译的（热点代码）进行编译




## 参考
- [什么是JIT](https://blog.csdn.net/shenwansangz/article/details/95601232)