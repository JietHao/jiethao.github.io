# Python规范

## 写好python函数的几点建议
> 引用自微信公众号文章：https://mp.weixin.qq.com/s/2AoovjvyWT3HGn2-M4chTg

1. 命名合理
   * 反例
     ```python
     def get_knn(from_df):
     ```
   * 建议
     ```python
     def get_k_nearest_neighbors(dataframe):
     ```
2. 单一功能
   * 反例
     ```python
     def calculate_and_print_stats():
     ```
   * 建议
     ```python
     def calculate_stats():

     def print_stats():
     ```
3. 包括文档字符串
   * 每个函数都需要有一个文档字符串
   * 使用适当的语法和标点符号；用完整的句子写
   * 首先对函数的作用进行一句话的总结
   * 使用说明性语言而不是描述性语言
4. 返回一个值
5. 不超过50行
6. 是幂等函数或纯函数
   * 不管被调用多少次，幂等函数总是在给定相同的参数集的情况下返回相同的值
   * 如果一个函数既幂等又没有可观察到的副作用，那么可以认为是纯函数。
   * 反例
     ```python
     def add_three():
         """Return 3 + the number entered by the user."""
         number = int(input('Enter a number'))
         return number + 3
     ```
   * 建议
     ```python
     def add_three(number):
         """Return *number* + 3."""
     ```