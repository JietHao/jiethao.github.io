# 编程范式（Progarming Paradigm）

是一类典型的编程风格。

- 命令式
- 声明式


## 命令式(Imperative)
- 关注计算机执行的步骤，即一步一步告诉先做什么再做什么
- 行动导向（Action-Oriented），算法是显性得的而目标是隐性的


## 声明式(Declarative)
- 告诉计算机应该做什么，但不指定具体要怎么做
- 目标驱动（Goal-Driven），目标是显性的而算法是隐性的
- 示例：SQL


### 函数式编程（Functional Programing, FP）

https://blog.csdn.net/juzipchy/article/details/77970375


- 函数是"第一等公民"(first class functions)
  - everything is a function
  - 函数与其他数据类型一样，处于平等地位，可以赋值给其他变量，也可以作为参数，传入另一个函数，或者作为别的函数的返回值。

- 无副作用（no side effects）
  - 所谓"副作用"（side effect），指的是函数内部与外部互动（最典型的情况，就是修改全局变量的值），产生运算以外的其他结果。
  - 函数式编程强调没有"副作用"，意味着函数要保持独立，所有功能就是返回一个新的值，没有其他行为，尤其是不得修改外部变量的值。

- 只用表达式，没有语句
  - "表达式"（expression）是一个单纯的运算过程，总是有返回值；"语句"（statement）是执行某种操作，没有返回值。
  - 函数式编程要求，只使用表达式，不使用语句。也就是说，每一步都是单纯的运算，而且都有返回值。

- 不修改状态
  - 函数式编程只是返回新的值，不修改系统变量。因此，不修改变量，也是它的一个重要特点。
  - 在其他类型的语言中，变量往往用来保存"状态"（state）。不修改变量，意味着状态不能保存在变量中。
  - 函数式编程使用参数保存状态，最好的例子就是递归。

- 引用透明（Referential transparency）
  - 引用透明（Referential transparency），指的是函数的运行不依赖于外部变量或"状态"，只依赖于输入的参数，任何时候只要参数相同，引用函数所得到的返回值总是相同的。





- 不可变性（immutable）



- 高阶函数（high-order function）
- 偏应用函数（Partially Applide Functions）
- 柯里化（currying）
- 闭包（closure）

- 惰性求值(Lazy ev)
- 引用透明性



### lambda演算
- 一套用于研究函数定义、函数应用和递归的形式系统
- 最早是由邱奇（Alonzo Church，图灵的博导）在20世纪30年代引入，当时的背景是解决函数可计算的本质性问题
- 是编程语言的基石
- 初期解决了在可计算理论中的判定性问题（http://en.wikipedia.org/wiki/Entscheidungsproblem）
- 后来根据Church–Turing thesis，证明了λ演算与图灵机是等价的。

http://cgnail.github.io/academic/lambda-1/


### 其他
- Continuation
- 延续传递风格 CPS (Continuation Pass Style)
  - 无需栈
  - 但是每次调用函数的时候都会要多加一个参数

- 示例：
  - 普通写法
    ```
    int i = add(5, 10)  // 15
    int j = square(i)   // 225
    ```
  - CPS写法
    ```
    int j = add(5, 10, square) // 225
    ```


### 代码示例
1. 示例1
```python
import sys

num = int(sys.argv[1])

ret = ((num + 3) * 5 - 1) % 10 / 2

print('((num + 3) * 5 - 1) % 10 / 2 的计算结果: ', ret)
```

2. 示例2
```python
import sys

def Add(i, j):
    return i + j

def Sub(i, j):
    return i - j

def Mul(i, j):
    return i * j

def Div(i, j):
    return i / j

def Mod(i, j):
    return i % j

num = int(sys.argv[1])

ret2 = Div(Mod(Sub(Mul(Add(num, 3), 5), 1), 10), 2)

print('\nDiv(Mod(Sub(Mul(Add(num, 3), 5), 1), 10): ', ret2,)
```

3. 示例3
```python
from ft2 import *

def Add3(i):
    return i + 3

def Mul5(i):
    return i * 5

def Sub1(i):
    return i - 1

def Mod10(i):
    return i % 10

def Div2(i):
    return i / 2

ret3 = Div2(Mod10(Sub1(Mul5(Add3(num)))))

print('\nDiv2(Mod10(Sub1(Mul5(Add3(num))))): 计算结果是：', ret3)
```

4. 示例4
```python
from ft3 import *

def Composite(fn1, fn2):
   return lambda i: fn2(fn1(i))

fn = Composite(Add3, Mul5)
fn = Composite(fn, Sub1)
fn = Composite(fn, Mod10)
fn = Composite(fn, Div2)
ret4 = fn(num)

print('\ncomposite fn(num): 计算结果是：', ret4)
```

5. 示例5
```python
from ft4 import *

def Currying(fn):
    return lambda j: lambda i: fn(i,j)

curryAdd = Currying(Add)
currySub = Currying(Sub)
curryMul = Currying(Mul)
curryDiv = Currying(Div)
curryMod = Currying(Mod)

add3 = curryAdd(3)
mul5 = curryMul(5)
sub1 = currySub(1)
div2 = curryDiv(2)
mod10 = curryMod(10)

cfn = Composite(add3, mul5)
cfn = Composite(cfn, sub1)
cfn = Composite(cfn, mod10)
cfn = Composite(cfn, div2)
ret5 = cfn(num)

print('\ncurrying cfn(num): 计算结果是：', ret5)
```

6. 示例6
```python
from ft5 import *

cfn1 = Composite(cfn, add3)
ret6 = cfn1(num)

print('\ncurrying ret6: 计算结果是：', ret6)

cfn2 = Composite(cfn1, currySub(3))
ret7 = cfn2(num)

print('\ncurrying ret7: 计算结果是：', ret7)
```
