

# 17 异常处理

## 异常处理

Python 使用 _try_ 和 _except_ 来优雅地处理错误。优雅地处理错误是一种简单的编程习惯 - 程序检测到严重错误条件并以受控的方式“优雅地退出”，通常作为结果，程序会将描述性错误消息打印到终端或日志中，这使得我们的应用程序更加健壮robust。异常的原因通常是程序本身之外的外部原因。异常的示例可能包括不正确的输入、错误的文件名、找不到文件、IO 设备故障等。优雅处理错误可以防止应用程序崩溃。

我们在前一节中介绍了不同的 Python _error_ 类型。如果在我们的程序中使用 _try_ 和 _except_，那么它不会在这些块中引发错误。

![尝试和捕获](./17_exception_handling - Copy.assets/try_except.png)

```py
try:
    如果一切顺利，请在此块中编写代码
except:
    如果出现问题，请在此块中运行代码
```

**示例：**

```py
try:
    print(10 + '5')
except:
    print('出错了')
```

在上面的示例中，第二个操作数是一个字符串。我们可以将其更改为浮点数或整数，以便与数字相加，以使其正常工作。但是，如果没有任何更改，将执行第二个块，即 _except_。

**示例：**

```py
try:
    name = input('请输入您的姓名：')
    year_born = input('您出生的年份：')
    age = 2019 - year_born
    print(f'您是{name}。您的年龄是{age}岁。')
except:
    print('出错了')
```

```sh
出错了
```

在上面的示例中，异常块将运行，我们不知道确切的问题是什么。要分析问题，我们可以使用 except 来处理不同的错误类型。

> input返回的是字符串，所以需要将字符串转换为整数。

在以下示例中，它将处理错误并告诉我们引发的错误类型。

```py
try:
    name = input('请输入您的姓名：')
    year_born = input('您出生的年份：')
    age = 2019 - year_born
    print(f'您是{name}。您的年龄是{age}岁。')
except TypeError:
    print('发生了类型错误')
except ValueError:
    print('发生了值错误')
except ZeroDivisionError:
    print('发生了零除错误')
```

```sh
请输入您的姓名：Asabeneh
您出生的年份：1920
发生了类型错误
```

在上面的代码中，输出将是 _TypeError_。
现在，让我们添加一个额外的块：

```py
try:
    name = input('请输入您的姓名：')
    year_born = input('您出生的年份：')
    age = 2019 - int(year_born)
    print('您是{name}。您的年龄是{age}岁。')
except TypeError:
    print('发生了类型错误')
except ValueError:
    print('发生了值错误')
except ZeroDivisionError:
    print('发生了零除错误')
else:
    print('我通常与 try 块一起运行')
finally:
    print('我总是运行。')
```

```sh
请输入您的姓名：Asabeneh
您出生的年份：1920
您是 Asabeneh。您的年龄是 99岁。
我通常与 try 块一起运行
我总是运行。
```

也可以将上述代码简化如下：

```py
try:
    name = input('请输入您的姓名：')
    year_born = input('您出生的年份：')
    age = 2019 - int(year_born)
    print('您是{name}。您的年龄是{age}岁。')
except Exception as e:
    print(e)

```

## 在 Python 中打包和解包参数

我们使用两个运算符：

- \* 用于元组或列表
- \*\* 用于字典

让我们以下面的示例为例。它只接受参数，但我们有一个列表。我们可以解包列表并更改为参数。

### 解包Unpacking

#### 解包列表

```py
def sum_of_five_nums(a, b, c, d, e):
    return a + b + c + d + e

lst = [1, 2, 3, 4, 5]
print(sum_of_five_nums(lst)) # TypeError: sum_of_five_nums() missing 4 required positional arguments: 'b', 'c', 'd', and 'e'
```

当我们运行这段代码时，它会引发错误，因为此函数需要作为参数的数字（而不是列表）。让我们解包/解构列表。

```py
def sum_of_five_nums(a, b, c, d, e):
    return a + b + c + d + e

lst = [1, 2, 3, 4, 5]
print(sum_of_five_nums(*lst))  # 15
```

我们还可以在预期开始和结束的 range 内置函数中使用解包。

```py
numbers = range(2, 7)  # 使用单独的参数进行普通调用
print(list(numbers)) # [2, 3, 4, 5, 6]
args = [2, 7]
numbers = range(*args)  # 使用从列表中解包的参数进行调用
print(numbers)      # [2, 3, 4, 5,6]

```

还可以像这样解包列表或元组：

```py
countries = ['芬兰', '瑞典', '挪威', '丹麦', '冰岛']
fin, sw, nor, *rest = countries
print(fin, sw, nor, rest)   # 芬兰 瑞典 挪威 ['丹麦', '冰岛']
numbers = [1, 2, 3, 4, 5, 6, 7]
one, *middle, last = numbers
print(one, middle, last)      #  1 [2, 3, 4, 5, 6] 7
```

#### 解包字典

```py
def unpacking_person_info(name, country, city, age):
    return f'{name} 居住在 {country}，{city}。他今年 {age} 岁了。'
dct = {'name':'Asabeneh', 'country':'Finland', 'city':'Helsinki', 'age':250}
print(unpacking_person_info(**dct)) # Asabeneh 居住在 Finland，Helsinki。他今年 250 岁了。
```

### 打包Packing

有时我们永远不知道需要传递给 Python 函数的参数数量。我们可以使用打包方法来允许我们的函数接受无限数量或任意数量的参数。

### 打包列表

```py
def sum_all(*args):
    s = 0
    for i in args:
        s += i
    return s
print(sum_all(1, 2, 3))             # 6
print(sum_all(1, 2, 3, 4, 5, 6, 7)) # 28
```

#### 打包字典

```py
def packing_person_info(**kwargs):
    # 检查 kwargs 的类型，它是 dict 类型
    # print(type(kwargs))
    # 打印字典项
    for key in kwargs:
        print(f"{key} = {kwargs[key]}")
    return kwargs

print(packing_person_info(name="Asabeneh",country="Finland", city="Helsinki", age=250))
```

```sh
name = Asabeneh
country = Finland
city = Helsinki
age = 250
{'name': 'Asabeneh', 'country': 'Finland', 'city': 'Helsinki', 'age': 250}
```

## Python 中的展开Spreading 

与 JavaScript 一样，Python 中也可以展开。让我们在下面的示例中检查它：

```py
lst_one = [1, 2, 3]
lst_two = [4, 5, 6, 7]
lst = [0, *lst_one, *lst_two]
print(lst)          # [0, 1, 2, 3, 4, 5, 6, 7]
country_lst_one = ['芬兰', '瑞典', '挪威']
country_lst_two = ['丹麦', '冰岛']
nordic_countries = [*country_lst_one, *country_lst_two]
print(nordic_countries)  # ['芬兰', '瑞典', '挪威', '丹麦', '冰岛']
```

## 枚举Enumerate

如果我们对列表的索引感兴趣，我们可以使用 _enumerate_ 内置函数来获取列表中每个项的索引。

```py
for index, item in enumerate([20, 30, 40]):
    print(index, item)
```

```py
for index, i in enumerate(countries):
    print('嗨')
    if i == '芬兰':
        print('国家 {i} 已在索引 {index} 处找到')
```

```sh
芬兰国家已在索引 1 处找到。
```

## 压缩Zip

有时，当我们循环遍历它们时，我们希望将列表合并在一起。看下面的示例：

```py
fruits = ['香蕉', '橙子', '芒果', '柠檬', '酸橙']                    
vegetables = ['番茄', '土豆', '卷心菜', '洋葱', '胡萝卜']
fruits_and_veges = []
for f, v in zip(fruits, vegetables):
    fruits_and_veges.append({'水果':f, '蔬菜':v})

print(fruits_and_veges)
```

```sh
[{'水果': '香蕉', '蔬菜': '番茄'}, {'水果': '橙子', '蔬菜': '土豆'}, {'水果': '芒果', '蔬菜': '卷心菜'}, {'水果': '柠檬', '蔬菜': '洋葱'}, {'水果': '酸橙', '蔬菜': '胡萝卜'}]
```

## 练习：第17天

1. names = ['芬兰', '瑞典', '挪威', '丹麦', '冰岛', '爱沙尼亚', '俄罗斯']。解包前五个国家并将它们存储在变量 nordic_countries 中，将爱沙尼亚和俄罗斯分别存储在 es 和 ru 中。
