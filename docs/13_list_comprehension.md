# 13 列表推导式

## 列表推导式

在Python中，列表推导是一种从序列中创建列表的简洁方法。它是创建新列表的一种简便方式。列表推导在性能上比使用`for`循环处理列表要快得多。

```py
# 语法
[i for i in iterable if expression]
```

**示例1**

例如，如果您想将字符串更改为字符列表，可以使用一些方法。让我们看看其中一些：

```py
# 一种方式
language = 'Python'
lst = list(language) # 将字符串更改为列表
print(type(lst))     # 列表
print(lst)           # ['P', 'y', 't', 'h', 'o', 'n']

# 第二种方式：列表推导
lst = [i for i in language]
print(type(lst)) # 列表
print(lst)       # ['P', 'y', 't', 'h', 'o', 'n']

```

**示例2**

例如，如果您想生成一个数字列表

```py
# 生成数字
numbers = [i for i in range(11)]  # 生成0到10的数字
print(numbers)                    # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

# 在迭代过程中执行数学运算也是可能的
squares = [i * i for i in range(11)]
print(squares)                    # [0, 1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

# 也可以创建一个元组列表
numbers = [(i, i * i) for i in range(11)]
print(numbers)                             # [(0, 0), (1, 1), (2, 4), (3, 9), (4, 16), (5, 25)]

```

**示例2**

列表推导可以与if表达式结合使用


```py
# 生成偶数
even_numbers = [i for i in range(21) if i % 2 == 0]  # 生成0到21范围内的偶数列表
print(even_numbers)                    # [0, 2, 4, 6, 8, 10, 12, 14, 16, 18, 20]

# 生成奇数
odd_numbers = [i for i in range(21) if i % 2 != 0]  # 生成0到21范围内的奇数
print(odd_numbers)                      # [1, 3, 5, 7, 9, 11, 13, 15, 17, 19]
# 过滤数字：让我们从以下列表中过滤出正偶数
numbers = [-8, -7, -3, -1, 0, 1, 3, 4, 5, 7, 6, 8, 10]
positive_even_numbers = [i for i in range(21) if i % 2 == 0 and i > 0]
print(positive_even_numbers)                    # [2, 4, 6, 8, 10, 12, 14, 16, 18, 20]

# 展平三维数组
list_of_lists = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
flattened_list = [ number for row in list_of_lists for number in row]
print(flattened_list)    # [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

## Lambda函数

Lambda函数是一种没有名称的小型匿名函数。它可以接受任意数量的参数，但只能有一个表达式。Lambda函数类似于JavaScript中的匿名函数。当我们想要在另一个函数内部编写匿名函数时，就需要使用它。

### 创建Lambda函数

要创建lambda函数，我们使用`lambda`关键字，后面跟参数（s），然后是一个表达式。请参阅下面的语法和示例。Lambda函数不使用`return`，但它显式返回表达式。

```py
# 语法
x = lambda param1, param2, param3: param1 + param2 + param2
print(x(arg1, arg2, arg3))
```

**示例:**

```py
# 命名函数
def add_two_nums(a, b):
    return a + b

print(add_two_nums(2, 3))     # 5
# 让我们将上述函数更改为lambda函数
add_two_nums = lambda a, b: a + b
print(add_two_nums(2,3))    # 5

# 自调用Self invoking lambda函数
(lambda a, b: a + b)(2,3) # 5 - 需要将其封装在print()中以在控制台中查看结果

square = lambda x : x ** 2
print(square(3))    # 9
cube = lambda x : x ** 3
print(cube(3))    # 27

# 多个变量
multiple_variable = lambda a, b, c: a ** 2 - 3 * b + 4 * c
print(multiple_variable(5, 5, 3)) # 22
```

### 在另一个函数内使用Lambda函数

在另一个函数内使用lambda函数。

```py
def power(x):
    return lambda n : x ** n

cube = power(2)(3)   # 现在函数power需要2个参数才能运行，在不同的圆括号中
print(cube)          # 8
two_power_of_five = power(2)(5) 
print(two_power_of_five)  # 32
```

## 💻 练习：第13天

1. 使用列表推导仅过滤列表中的负数和零

   ```py
   numbers = [-4, -3, -2, -1, 0, 2, 4, 6]
   ```

2. 将以下列表的列表的列表展平为一维列表：

   ```py
   list_of_lists =[[[1, 2, 3]], [[4, 5, 6]], [[7, 8, 9]]]
   
   输出
   [1, 2, 3, 4, 5, 6, 7, 8, 9]
   ```

3. 使用列表推导创建以下元组的列表：

   ```py
   [(0, 1, 0, 0, 0, 0, 0),
   (1, 1, 1, 1, 1, 1, 1),
   (2, 1, 2, 4, 8, 16, 32),
   (3, 1, 3, 9, 27, 81, 243),
   (4, 1, 4, 16, 64, 256, 1024),
   (5, 1, 5, 25, 125, 625, 3125),
   (6, 1, 6, 36, 216, 1296, 7776),
   (7, 1, 7, 49, 343, 2401, 16807),
   (8, 1, 8, 64, 512, 4096, 32768),
   (9, 1, 9, 81, 729, 6561, 59049),
   (10, 1, 10, 100, 1000, 10000, 100000)]
   ```

4. 将以下列表展平为一个新列表：

   ```py
   countries = [[('Finland', 'Helsinki')], [('Sweden', 'Stockholm')], [('Norway', 'Oslo')]]
   输出:
   [['FINLAND','FIN', 'HELSINKI'], ['SWEDEN', 'SWE', 'STOCKHOLM'], ['NORWAY', 'NOR', 'OSLO']]
   ```

5. 将以下列表更改为字典列表：

   ```py
   countries = [[('Finland', 'Helsinki')], [('Sweden', 'Stockholm')], [('Norway', 'Oslo')]]
   输出:
   [{'country': 'FINLAND', 'city': 'HELSINKI'},
   {'country': 'SWEDEN', 'city': 'STOCKHOLM'},
   {'country': 'NORWAY', 'city': 'OSLO'}]
   ```

6. 将以下列表的列表更改为连接的字符串列表：

   ```py
   names = [[('Asabeneh', 'Yetayeh')], [('David', 'Smith')], [('Donald', 'Trump')], [('Bill', 'Gates')]]
   输出
   ['Asabeneh Yetaeyeh', 'David Smith', 'Donald Trump', 'Bill Gates']
   ```

7. 编写一个能够解决线性函数的斜率或y截距的lambda函数。
