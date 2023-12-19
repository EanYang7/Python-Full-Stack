# 02 变量，内置函数

## 内置函数

在Python中，我们有许多内置函数。内置函数是全局可用的，这意味着您可以在不导入或配置的情况下使用内置函数。以下是一些最常用的Python内置函数：_print()_、_len()_、_type()_、_int()_、_float()_、_str()_、_input()_、_list()_、_dict()_、_min()_、_max()_、_sum()_、_sorted()_、_open()_、_file()_、_help()_ 和 _dir()_。在下表中，您将看到来自[Python文档](https://docs.python.org/3.9/library/functions.html)的Python内置函数的详尽列表。

![内置函数](./images/builtin-functions.png)

让我们打开Python shell并开始使用一些最常见的内置函数。

![内置函数](./images/builtin-functions_practice.png)

让我们通过使用不同的内置函数进行更多练习。

![内置函数Help和Dir](./images/help_and_dir_builtin.png)

正如您从上面的终端中看到的，Python有保留字reserved words。我们不使用保留字来声明变量或函数。我们将在下一节中介绍变量。

我相信，到目前为止，您已经熟悉了内置函数。让我们再练习一下内置函数，然后我们将进入下一节。

![Min Max Sum](./images/builtin-functional-final.png)

## 变量

变量在计算机内存中存储数据。建议在许多编程语言中使用助记符变量。助记符变量是一个易于记忆和关联的变量名称。变量指的是存储数据的内存地址。
在命名变量时不允许在变量名中以数字、特殊字符或连字符开头。变量可以具有短名称（如x、y、z），但强烈建议使用更具描述性的名称（firstname、lastname、age、country）。

Python变量名称规则

- 变量名必须以字母或下划线字符开头
- 变量名不能以数字开头
- 变量名只能包含字母数字字符和下划线（A-z、0-9和\_）
- 变量名区分大小写（firstname、Firstname、FirstName和FIRSTNAME是不同的变量）

以下是一些有效变量名称的示例：

```shell
firstname
lastname
age
country
city
first_name
last_name
capital_city
_if # 如果要将保留字用作变量
year_2021
year2021
current_year_2021
birth_year
num1
num2
```

无效的变量名称

```shell
first-name
first@name
first$name
num-1
1num
```

我们将使用许多Python开发人员采用的标准Python变量命名样式。Python开发人员使用（snake_case）变量命名约定。对于包含多个单词的变量，我们在每个单词之后使用下划线字符（例如，first_name、last_name、engine_rotation_speed）。下面的示例是变量的标准命名示例，变量名包含多个单词时需要使用下划线。

>Python 也推荐使用驼峰式命名(camelCase)，那是在类名、Type 变量、异常 exception 名这些情况。而在**包名、模块名、方法名和普通变量名**等情况，则是推荐用蛇形命名

当我们将某种数据类型分配给变量时，称之为变量声明。例如，在下面的示例中，我的名字被分配给了变量first_name。等号是一个赋值运算符。分配意味着将数据存储在变量中。在Python中，等号不等同于数学中的等号。

_示例：_

```py
# Python中的变量
first_name = 'Asabeneh'
last_name = 'Yetayeh'
country = 'Finland'
city = 'Helsinki'
age = 250
is_married = True
skills = ['HTML', 'CSS', 'JS', 'React', 'Python']
person_info = {
   'firstname':'Asabeneh',
   'lastname':'Yetayeh',
   'country':'Finland',
   'city':'Helsinki'
   }
```

让我们使用内置函数 _print()_ 和 _len()_。打印函数接受无限数量的参数。参数是可以传递或放入函数括号内的值，参见下面的示例。

**示例：**

```py
print('Hello, World!') # 文本Hello, World!是一个参数
print('Hello',',', 'World','!') # 它可以接受多个参数，已传递了四个参数
print(len('Hello, World!')) # 它只接受一个参数
```

让我们打印并查找在顶部声明的变量的长度：

**示例：**

```py
# 打印存储在变量中的值

print('First name:', first_name)
print('First name length:', len(first_name))
print('Last name: ', last_name)
print('Last name length: ', len(last_name))
print('Country: ', country)
print('City: ', city)
print('Age: ', age)
print('Married: ', is_married)
print('Skills: ', skills)
print('Person information: ', person_info)
```

### 在一行中声明多个变量

多个变量也可以在一行中声明：

**示例：**

```py
first_name, last_name, country, age, is_married = 'Asabeneh', 'Yetayeh', 'Helsink', 250, True

print(first_name, last_name, country, age, is_married)
print('First name:', first_name)
print('Last name: ', last_name)
print('Country: ', country)
print('Age: ', age)
print('Married: ', is_married)
```

使用内置的_input()_函数获取用户输入。让我们将从用户那里获取的数据分配给first_name和age变量。
**示例：**

```py
first_name = input('What is your name: ')
age = input('How old are you? ')

print(first_name)
print(age)
```

## 数据类型

Python中有几种数据类型。要识别数据类型，我们使用_type_内置函数。我想请您专注于很好地理解不同的数据类型。在编程方面，一切都与数据类型有关。我在最初引入了数据类型，因为每个主题都与数据类型相关。我们将在各自的章节中更详细地介绍数据类型。

## 检查数据类型和强制类型转换

- 检查数据类型：要检查某个数据/变量的数据类型，我们使用_type_
  **示例：**

```py
# 不同的Python数据类型
# 让我们声明具有各种数据类型的变量

first_name = 'Asabeneh'     # str
last_name = 'Yetayeh'       # str
country = 'Finland'         # str
city= 'Helsinki'            # str
age = 250                   # int

# 打印类型
print(type('Asabeneh'))     # str
print(type(first_name))     # str
print(type(10))             # int
print(type(3.14))           # float
print(type(1 + 1j))         # complex
print(type(True))           # bool
print(type([1, 2, 3, 4]))     # list
print(type({'name':'Asabeneh','age':250, 'is_married':250}))    # dict
print(type((1,2)))                                              # tuple
print(type(zip([1,2],[3,4])))                                   # set
```

- 强制类型转换：将一种数据类型转换为另一种数据类型。我们使用_int()_、_float()_、_str()_、_list_、_set_
  当我们执行字符串数字的算术运算时，应首先将字符串数字转换为int或float，否则会返回错误。如果我们将数字与字符串连接，那么数字应首先转换为字符串。我们将在字符串部分讨论连接。

  **示例：**

```py
# int to float
num_int = 10
print('num_int',num_int)         # 10
num_float = float(num_int)
print('num_float:', num_float)   # 10.0

# float to int
gravity = 9.81
print(int(gravity))             # 9

# int to str
num_int = 10
print(num_int)                  # 10
num_str = str(num_int)
print(num_str)                  # '10'

# str to int or float
num_str = '10.6'
print('num_int', int(num_str))      # 10
print('num_float', float(num_str))  # 10.6

# str to list
first_name = 'Asabeneh'
print(first_name)               # 'Asabeneh'
first_name_to_list = list(first_name)
print(first_name_to_list)            # ['A', 's', 'a', 'b', 'e', 'n', 'e', 'h']
```

## 数字

Python中的数字数据类型：

1. 整数：整数（负数、零和正数）
   示例：
   ... -3, -2, -1, 0, 1, 2, 3 ...

2. 浮点数（小数）
   示例：
   ... -3.5, -2.25, -1.0, 0.0, 1.1, 2.2, 3.5 ...

3. 复数
   示例：
   1 + j, 2 + 4j, 1 - 1j

🌕 你很棒。您刚刚完成了第2天的挑战，距离伟大还有两步。现在为您的大脑和肌肉做一些练习。

## 💻 练习 - 第2天

### 练习：Level 1

1. 在30DaysOfPython中创建一个名为day_2的文件夹。在此文件夹内创建一个名为variables.py的文件。
2. 编写一个Python注释，写上'Day 2: 30 Days of Python programming'。
3. 声明一个名为first_name的变量，并为其赋一个值。
4. 声明一个名为last_name的变量，并为其赋一个值。
5. 声明一个名为full_name的变量，并为其赋一个值。
6. 声明一个名为country的变量，并为其赋一个值。
7. 声明一个名为city的变量，并为其赋一个值。
8. 声明一个名为age的变量，并为其赋一个值。
9. 声明一个名为year的变量，并为其赋一个值。
10. 声明一个名为is_married的变量，并为其赋一个值。
11. 声明一个名为is_true的变量，并为其赋一个值。
12. 声明一个名为is_light_on的变量，并为其赋一个值。
13. 在一行中声明多个变量。

### 练习：Level 2

1. 使用type()内置函数检查所有变量的数据类型。
2. 使用_len()_内置函数，查找您的名字的长度。
3. 比较您的名字的长度和您的姓氏的长度。
4. 将5分别声明为num_one，4为num_two。
   1. 将num_one和num_two相加，并将值赋给一个名为total的变量。
   2. 从num_one中减去num_two，并将值赋给一个名为diff的变量。
   3. 将num_two和num_one相乘，并将值赋给一个名为product的变量。
   4. 将num_one除以num_two，并将值赋给一个名为division的变量。
   5. 使用模运算找到num_two除以num_one的值，并将其赋给一个名为remainder的变量。
   6. 计算num_one的num_two次方，并将值赋给一个名为exp的变量。
   7. 找到num_one除以num_two的地板除法，并将值赋给一个名为floor_division的变量。
5. 一个圆的半径是30米。
   1. 计算圆的面积并将该值分配给变量名为 _area_of_circle_
   2. 计算圆的周长并将该值分配给变量名为 _circum_of_circle_
   3. 接受用户输入的半径并计算面积。
6. 使用内置的 input 函数从用户那里获取名字、姓氏、国家和年龄，并将这些值存储到相应的变量名中。
7. 在Python shell或您的文件中运行 help('keywords') 来检查Python的保留字或关键字。

