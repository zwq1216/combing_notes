# Python梳理

## 1. 前言

这次的梳理并不会像基础入门一样，从变量、函数、类等基本语法开始梳理，而是参照《流畅的Python》一书进行梳理，结合自己的理解加以应用写一些实例。目的在于理清自己混乱的知识储备，为下一步深入理解Python准备。

## 2. 数据结构

### 2.1 内置序列

容器序列：list、tuple和collections.deque这些序列能存放不同类型的数据。

扁平序列：str、bytes、bytearray、memoryview和array.array这些只能一种类型的数据。

容器序列和扁平序列的区别：容器序列存放的是他们所包含的任意类型对象的引用。而扁平序列则存放的是值而不是引用。

### 2.2 列表推导和生成器表达式

#### 2.2.1 列表推导

目的：生成列表

生成结果：列表

优点：可读性强、效率高

需要一个列表，列表里有3种不同尺寸的T恤衫，每个尺寸都有2个颜色，推算出这个列表。

```colors = ['black', 'white']
sizes = ['S', 'M', 'L']

tshirts = [(size, color) for size in sizes for color in colors]

print(tshirts)
```

结果：

```[('S', 'black'), ('S', 'white'), ('M', 'black'), ('M', 'white'), ('L', 'black'), ('L', 'white')]```

关于Python2.x中变量泄漏问题，实例如下图：

![alt 变量泄漏](C:\Users\ASUS\Desktop\2.png)

如图中所见x的值被取代了，<b>所以在Python2.x中使用时请注意</b>。此问题在Python3中不存在。

#### 2.2.2 生成器表达式

目的：初始化序列（各种序列），比如元组、数组等

实现：将列表推导式的中括号换成圆括号

生成结果：可迭代对象

优点：节省内存

应用典例（笛卡尔积）描述如下：

需要一个列表，列表里有3种不同尺寸的T恤衫，每个尺寸都有2个颜色，推算出这个列表。

```colors = ['black', 'white']
sizes = ['S', 'M', 'L']

tshirts = ((size, color) for size in sizes for color in colors)

for t in tshirts:
    print(t)
```

结果：

```('S', 'black')
('S', 'black')
('S', 'white')
('M', 'black')
('M', 'white')
('L', 'black')
('L', 'white')
```

<b>注意：当生成器表达式作为参数传递时如果仅传递该表达式则可以不写圆括号</b>

* 切片
* 排序（sorted）
* 数组
* 内存视图
* 队列

## 3 字典与集合

