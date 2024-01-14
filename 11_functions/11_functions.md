# 11 函数

## 函数

到目前为止，我们已经看到了许多内置的Python函数。在本节中，我们将关注自定义函数。什么是函数？在我们开始创建函数之前，让我们学习一下函数是什么以及为什么需要它们？

### 定义函数

函数是一块可重复使用的代码块或编程语句，旨在执行某个特定的任务。要定义或声明一个函数，Python提供了`def`关键字。以下是定义函数的语法。只有在调用或调用函数时，函数的代码块才会被执行。

### 声明和调用函数

当我们创建一个函数时，我们称之为声明函数。当我们开始使用它时，我们称之为*调用(*calling/ *invoking*)函数。函数可以带参数或不带参数。

```py
# 语法
# 声明一个函数
def function_name():
    代码
    代码
# 调用一个函数
function_name()
```

### 无参数的函数

函数可以在不带参数的情况下声明。

**示例：**

```py
def generate_full_name():
    first_name = 'Asabeneh'
    last_name = 'Yetayeh'
    space = ' '
    full_name = first_name + space + last_name
    print(full_name)
generate_full_name() # 调用一个函数

def add_two_numbers():
    num_one = 2
    num_two = 3
    total = num_one + num_two
    print(total)
add_two_numbers()
```

### 有返回值的函数 - 第1部分

函数也可以返回值，如果一个函数没有返回语句，函数的值就是None。现在，让我们使用return来重写上面的函数。从现在开始，我们在调用函数时从函数中获取一个值并打印它。

```py
def generate_full_name():
    first_name = 'Asabeneh'
    last_name = 'Yetayeh'
    space = ' '
    full_name = first_name + space + last_name
    return full_name
print(generate_full_name())

def add_two_numbers():
    num_one = 2
    num_two = 3
    total = num_one + num_two
    return total
print(add_two_numbers())
```

### 带参数的函数

在函数中，我们可以将不同的数据类型（数字、字符串、布尔值、列表、元组、字典或集合）作为参数传递

- 单个参数：如果我们的函数带有参数，我们应该使用一个参数来调用我们的函数

```py
  # 语法
  # 声明一个函数
  def function_name(parameter):
    代码
    代码
  # 调用函数
  print(function_name(argument))
```

**示例：**

```py
def greetings(name):
    message = name + '，欢迎来到Python for Everyone！'
    return message

print(greetings('Asabeneh'))

def add_ten(num):
    ten = 10
    return num + ten
print(add_ten(90))

def square_number(x):
    return x * x
print(square_number(2))

def area_of_circle(r):
    PI = 3.14
    area = PI * r ** 2
    return area
print(area_of_circle(10))

def sum_of_numbers(n):
    total = 0
    for i in range(n+1):
        total+=i
    print(total)
print(sum_of_numbers(10)) # 55
print(sum_of_numbers(100)) # 5050
```

- 两个参数：一个函数可以有参数也可以没有参数。一个函数也可以有两个或更多的参数。如果我们的函数有参数，我们应该用参数来调用它。让我们看一个带有两个参数的函数：

```py
  # 语法
  # 声明一个函数
  def function_name(para1, para2):
    代码
    代码
  # 调用函数
  print(function_name(arg1, arg2))
```

**示例：**

```py
def generate_full_name(first_name, last_name):
    space = ' '
    full_name = first_name + space + last_name
    return full_name
print('全名：', generate_full_name('Asabeneh','Yetayeh'))

def sum_two_numbers(num_one, num_two):
    sum = num_one + num_two
    return sum
print('两个数字的和：', sum_two_numbers(1, 9))

def calculate_age(current_year, birth_year):
    age = current_year - birth_year
    return age;

print('年龄：', calculate_age(2021, 1819))

def weight_of_object(mass, gravity):
    weight = str(mass * gravity)+ ' N' # 将值首先更改为字符串
    return weight
print('牛顿下的物体重量：', weight_of_object(100, 9.81))
```

### 使用键和值传递参数

如果我们使用键和值传递参数，参数的顺序就不重要了。

```py
# 语法
# 声明一个函数
def function_name(para1, para2):
    代码
    代码
# 调用函数
print(function_name(para1 = 'John', para2 = 'Doe')) # 参数的顺序在这里不重要
```

**示例：**

```py
def print_fullname(firstname, lastname):
    space = ' '
    full_name = firstname  + space + lastname
    print(full_name)
print(print_fullname(firstname = 'Asabeneh', lastname = 'Yetayeh'))

def add_two_numbers(num1, num2):
    total = num1 + num2
    print(total)
print(add_two_numbers(num2 = 3, num1 = 2)) # 顺序不重要
```

### 有返回值的函数 - 第2部分

如果我们不使用函数返回值，那么默认情况下我们的函数将返回`None`。为了从函数中返回一个值，我们使用关键字`return`后跟我们要返回的变量。我们可以从函数中返回任何类型的数据。

- 返回一个字符串：
  **示例：**

```py
def print_name(firstname):
    return firstname
print_name('Asabeneh') # Asabeneh

def print_full_name(firstname, lastname):
    space = ' '
    full_name = firstname  + space + lastname
    return full_name
print_full_name(firstname='Asabeneh', lastname='Yetayeh')
```

- 返回一个数字:

**示例：**

```py
def add_two_numbers(num1, num2):
    total = num1 + num2
    return total
print(add_two_numbers(2, 3))

def calculate_age(current_year, birth_year):
    age = current_year - birth_year
    return age;
print('年龄：', calculate_age(2019, 1819))
```

- 返回一个布尔值：
  **示例：**

```py
def is_even(n):
    if n % 2 == 0:
        print('偶数')
        return True    # return会停止函数的进一步执行，类似于break
    return False
print(is_even(10)) # True
print(is_even(7)) # False
```

- 返回一个列表：
  **示例：**

```py
def find_even_numbers(n):
    evens = []
    for i in range(n + 1):
        if i % 2 == 0:
            evens.append(i)
    return evens
print(find_even_numbers(10))
```

### 具有默认参数的函数

有时，当我们调用函数时，我们会传递默认值给参数。如果我们在调用函数时不传递参数，那么参数的默认值将被使用。

```py
# 语法
# 声明一个函数
def function_name(param = value):
    代码
    代码
# 调用函数
function_name()
function_name(arg)
```

**示例：**

```py
def greetings(name = 'Peter'):
    message = name + '，欢迎来到Python for Everyone！'
    return message
print(greetings())
print(greetings('Asabeneh'))

def generate_full_name(first_name = 'Asabeneh', last_name = 'Yetayeh'):
    space = ' '
    full_name = first_name + space + last_name
    return full_name

print(generate_full_name())
print(generate_full_name('David','Smith'))

def calculate_age(birth_year, current_year = 2021):
    age = current_year - birth_year
    return age;
print('年龄：', calculate_age(1821))

def weight_of_object(mass, gravity = 9.81):
    weight = str(mass * gravity)+ ' N' # 将值首先更改为字符串
    return weight
print('牛顿下的物体重量：', weight_of_object(100)) # 9.81 - 地表上的平均重力
print('牛顿下的物体重量：', weight_of_object(100, 1.62)) # 月球表面上的重力
```

### 任意数量的参数

如果我们不知道要传递给函数的参数数量，我们可以通过在参数名之前添加\*来创建一个可以接受任意数量参数的函数。

```py
# 语法
# 声明一个函数
def function_name(*args):
    代码
    代码
# 调用函数
function_name(param1, param2, param3,..)
```

**示例：**

```py
def sum_all_nums(*nums):
    total = 0
    for num in nums:
        total += num     # 相当于 total = total + num
    return total
print(sum_all_nums(2, 3, 5)) # 10
```

### 函数中的默认参数和任意数量的参数

```py
def generate_groups(*args, team='Default Team'):
    print(team)
    for i in args:
        print(i)

generate_groups('Asabeneh', 'Brook', 'David', 'Eyob')
```

```
Default Team
Asabeneh
Brook
David
Eyob
```

### 函数作为另一个函数的参数

```py
# 您可以将函数作为参数传递
def square_number(n):
    return n * n
def do_something(f, x):
    return f(x)
print(do_something(square_number, 3)) # 9
```

## 💻 练习：第11天

### 练习：级别1

1. 声明一个名为_add_two_numbers_的函数。它接受两个参数并返回它们的和。
2. 圆的面积计算如下：面积 = π x r x r。编写一个计算_area_of_circle的函数。
3. 编写一个名为add_all_nums的函数，它接受任意数量的参数并求它们的总和。检查列表中的所有项目是否都是数字类型。如果不是，请给出合理的反馈。
4. 摄氏度可以使用以下公式转换为华氏度：°F = (°C x 9/5) + 32。编写一个将°C转换为°F的函数_convert_celsius_to_fahrenheit_。
5. 编写一个名为check_season的函数，它接受一个月份参数并返回季节：秋季、冬季、春季或夏季。
6. 编写一个名为calculate_slope的函数，它返回线性方程的斜率。
7. 二次方程计算如下：ax² + bx + c = 0。编写一个计算二次方程解集的函数_solve_quadratic_eqn_。
8. 声明一个名为print_list的函数。它接受一个列表作为参数，并打印出列表的每个元素。
9. 声明一个名为reverse_list的函数。它接受一个数组作为参数，并返回数组的反转版本（使用循环）。

```py
print(reverse_list([1, 2, 3, 4, 5]))
# [5, 4, 3, 2, 1]
print(reverse_list1(["A", "B", "C"]))
# ["C", "B", "A"]
```

10. 声明一个名为capitalize_list_items的函数。它接受一个列表作为参数，并返回首字母大写的项目列表。
11. 声明一个名为add_item的函数。它接受一个列表和一个项目作为参数。它返回一个在列表末尾添加了项目的列表。

```py
food_staff = ['Potato', 'Tomato', 'Mango', 'Milk'];
print(add_item(food_staff, 'Meat'))     # ['Potato', 'Tomato', 'Mango', 'Milk','Meat'];
numbers = [2, 3, 7, 9];
print(add_item(numbers, 5))      [2, 3, 7, 9, 5]
```

12. 声明一个名为remove_item的函数。它接受一个列表和一个项目作为参数。它返回一个从中删除了项目的列表。

```py
food_staff = ['Potato', 'Tomato', 'Mango', 'Milk'];
print(remove_item(food_staff, 'Mango'))  # ['Potato', 'Tomato', 'Milk'];
numbers = [2, 3, 7, 9];
print(remove_item(numbers, 3))  # [2, 7, 9]
```

13. 声明一个名为sum_of_numbers的函数。它接受一个数字参数并将该范围内的所有数字相加。

```py
print(sum_of_numbers(5))  # 15
print(sum_all_numbers(10)) # 55
print(sum_all_numbers(100)) # 5050
```

14. 声明一个名为sum_of_odds的函数。它接受一个数字参数并将该范围内的所有奇数相加。
15. 声明一个名为sum_of_even的函数。它接受一个数字参数并将该范围内的所有偶数相加。

### 练习：级别2

1. 声明一个名为evens_and_odds的函数。它接受一个正整数作为参数，并统计数字中的偶数和奇数个数。

```py
    print(evens_and_odds(100))
    # 奇数的数量为50。
    # 偶数的数量为51。
```

2. 调用您的函数factorial，它接受一个整数作为参数，并返回该数字的阶乘。
3. 调用您的函数_is_empty_，它接受一个参数并检查它是否为空。
4. 编写不同的函数，它们接受列表作为参数。它们应该计算均值、中位数、众数、范围、方差和标准差。

### 练习：级别3

1. 编写一个名为is_prime的函数，它检查一个数是否为质数。
2. 编写一个函数，检查列表中的所有项目是否都是唯一的。
3. 编写一个函数，检查列表中的所有项目是否都属于相同的数据类型。
4. 编写一个函数，检查提供的变量是否是有效的Python变量。
5. 转到数据文件夹并访问countries-data.py文件。

- 创建一个名为most_spoken_languages_in_the_world的函数。它应返回世界上最常用的10或20种语言，按降序排列。
- 创建一个名为most_populated_countries的函数。它应返回世界上最多人口的10或20个国家，按降序排列。
