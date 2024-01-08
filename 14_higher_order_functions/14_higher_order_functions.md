# 14 高阶函数

## 高阶函数Higher Order Functions

在Python中，函数被视为一等公民，允许您在函数上执行以下操作：

- 函数可以接受一个或多个函数作为参数
- 函数可以分配给变量
- 函数可以作为另一个函数的结果返回

??? note "详解"

    函数可以作为另一个函数的结果返回意味着在编程中，一个函数可以在其内部定义并返回另一个函数。这意味着函数可以被当作一种值来处理，可以像其他数据类型一样传递和使用。这种编程概念被称为**高阶函数**，它允许在运行时动态生成函数。
    
    以下是一个示例，说明了函数作为另一个函数的结果返回的概念：
    
    ```python
    def multiplier(factor):
        # 这是一个内部函数，它将被返回
        def multiply(x):
            return x * factor
        # 返回内部函数
        return multiply
    
    # 创建一个名为double的函数，它是multiplier(2)的结果
    double = multiplier(2)
    # 创建一个名为triple的函数，它是multiplier(3)的结果
    triple = multiplier(3)
    
    # 使用double函数
    result1 = double(5)  # 结果为10，因为double是multiplier(2)返回的函数，所以相当于调用multiply(5)
    print(result1)
    
    # 使用triple函数
    result2 = triple(5)  # 结果为15，因为triple是multiplier(3)返回的函数，所以相当于调用multiply(5)
    print(result2)
    ```
    
    在上面的示例中，`multiplier`函数接受一个参数`factor`，并返回一个新的函数`multiply`，该函数将`factor`应用于其参数。当我们调用`multiplier(2)`时，它返回一个新的函数`double`，该函数将参数乘以2。同样，调用`multiplier(3)`时返回一个新的函数`triple`，该函数将参数乘以3。然后，我们可以使用这些返回的函数来执行相应的操作，这展示了函数作为另一个函数的结果返回的概念。

- 函数可以被修改

??? note "详解"

    函数可以被修改意味着函数的行为和功能可以在运行时被改变，通常是通过修改函数的定义或在运行时修改函数的属性。这使得函数可以根据需要动态适应不同的情况或要求，增加了灵活性和可扩展性。
    
    以下是一个示例，说明了函数可以被修改的概念：
    
    ```python
    # 定义一个简单的函数
    def greet(name):
        return f"Hello, {name}!"
    
    # 定义一个修改函数的函数
    def modify_greet(func):
        def new_greet(name):
            # 在原始函数的基础上添加一些额外的内容
            message = func(name)
            return f"{message} How are you today?"
        return new_greet
    
    # 使用原始的greet函数
    original_greet = greet("Alice")
    print(original_greet)  # 输出：Hello, Alice!
    
    # 使用修改后的greet函数
    modified_greet = modify_greet(greet)
    new_message = modified_greet("Bob")
    print(new_message)  # 输出：Hello, Bob! How are you today?
    ```
    
    在上面的示例中，我们首先定义了一个简单的`greet`函数，它接受一个名字作为参数并返回问候语。然后，我们定义了一个名为`modify_greet`的函数，它接受一个函数作为参数，并返回一个新的函数，该新函数在原始函数的基础上添加了额外的内容。最后，我们使用原始的`greet`函数和修改后的`greet`函数来演示函数可以被修改的概念。

在本节中，我们将涵盖以下内容：

1. 处理函数作为参数
2. 从另一个函数返回函数作为返回值
3. 使用Python闭包和装饰器

### 函数作为参数

```py
def sum_numbers(nums):  # 普通函数
    return sum(nums)    # 滥用内置的sum函数,不够优雅、恰当

def higher_order_function(f, lst):  # 函数作为参数
    summation = f(lst)
    return summation
result = higher_order_function(sum_numbers, [1, 2, 3, 4, 5])
print(result)       # 15
```

### 函数作为返回值

```py
def square(x):          # 平方函数
    return x ** 2

def cube(x):            # 立方函数
    return x ** 3

def absolute(x):        # 绝对值函数
    if x >= 0:
        return x
    else:
        return -(x)

def higher_order_function(type): # 返回函数的高阶函数
    if type == 'square':
        return square
    elif type == 'cube':
        return cube
    elif type == 'absolute':
        return absolute

result = higher_order_function('square')
print(result(3))       # 9
result = higher_order_function('cube')
print(result(3))       # 27
result = higher_order_function('absolute')
print(result(-3))      # 3
```

您可以从上面的示例看到，高阶函数根据传递的参数返回不同的函数。

## Python闭包Closures

Python允许嵌套函数访问封闭enclosing函数的外部作用域。这被称为闭包Closure。让我们看看Python中闭包的工作原理。在Python中，通过将一个函数嵌套在另一个封装函数内部然后返回内部函数来创建闭包。请参阅下面的示例。

**示例：**

```py
def add_ten():
    ten = 10
    def add(num):
        return num + ten
    return add

closure_result = add_ten()
print(closure_result(5))  # 15
print(closure_result(10))  # 20
```

## Python装饰器Decorators

装饰器是Python中的一种设计模式，允许用户在不修改其结构的情况下向现有对象添加新功能。通常在要装饰的函数定义之前调用装饰器。

### 创建装饰器

要创建装饰器函数，我们需要一个具有内部包装函数的外部函数。

**示例：**

```py
# 普通函数
def greeting():
    return 'Welcome to Python'
def uppercase_decorator(function):
    def wrapper():
        func = function()
        make_uppercase = func.upper()
        return make_uppercase
    return wrapper
g = uppercase_decorator(greeting)
print(g())          # WELCOME TO PYTHON

## 让我们使用装饰器来实现上面的示例

'''这个装饰器函数是一个高阶函数
接受一个函数作为参数'''
def uppercase_decorator(function):
    def wrapper():
        func = function()
        make_uppercase = func.upper()
        return make_uppercase
    return wrapper
@uppercase_decorator
def greeting():
    return 'Welcome to Python'
print(greeting())   # WELCOME TO PYTHON

```

### 将多个装饰器应用于单个函数

```py
'''这些装饰器函数是高阶函数
接受函数作为参数'''

# 第一个装饰器
def uppercase_decorator(function):
    def wrapper():
        func = function()
        make_uppercase = func.upper()
        return make_uppercase
    return wrapper

# 第二个装饰器
def split_string_decorator(function):
    def wrapper():
        func = function()
        splitted_string = func.split()
        return splitted_string

    return wrapper

@split_string_decorator
@uppercase_decorator     # 在这种情况下，装饰器的顺序很重要 - .upper()函数不适用于列表
def greeting():
    return 'Welcome to Python'
print(greeting())   # ['WELCOME', 'TO', 'PYTHON']
```
> 先`@uppercase_decorator`再`@split_string_decorator`
### 在装饰器函数中接受参数

大多数情况下，我们需要函数接受参数，因此我们可能需要定义一个接受参数的装饰器。

```py
def decorator_with_parameters(function):
    def wrapper_accepting_parameters(para1, para2, para3):
        function(para1, para2, para3)
        print("I live in {}".format(para3))
    return wrapper_accepting_parameters

@decorator_with_parameters
def print_full_name(first_name, last_name, country):
    print("I am {} {}. I love to teach.".format(
        first_name, last_name, country))

print_full_name("Asabeneh", "Yetayeh",'Finland')
#I am Asabeneh Yetayeh. I love to teach.
#I live in Finland
```

## 内置高阶函数

我们在本部分中涵盖的一些内置高阶函数是`map()`，`filter`和`reduce`。
Lambda函数可以作为参数传递，lambda函数在map、filter和reduce等函数中的最佳用途。

### Python - Map函数

`map()`函数是一个内置函数，它接受一个函数和一个可迭代对象作为参数。

```py
# 语法
map(function, iterable)
```

**示例：1**

```py
numbers = [1, 2, 3, 4, 5] # 可迭代对象
def square(x):
    return x ** 2
numbers_squared = map(square, numbers)
print(list(numbers_squared))    # [1, 4, 9, 16, 25]
# 让我们使用lambda函数来应用它
numbers_squared = map(lambda x : x ** 2, numbers)
print(list(numbers_squared))    # [1, 4, 9, 16, 25]
```

!!! note "为什么使用`list`"

    在上面的代码中，我们使用 `map` 函数将一个函数 `square` 应用于可迭代对象 `numbers` 中的每个元素，生成一个新的可迭代对象 `numbers_squared`，其中每个元素都是原始元素经过 `square` 函数处理后的结果。然而，`numbers_squared` 本身也是一个可迭代对象，它不会立即生成结果，而是按需生成。
    
    为了获取最终的结果并将其打印出来，我们使用 `list()` 函数将 `numbers_squared` 转换为一个列表。`list()` 函数将可迭代对象中的所有元素生成并存储到列表中，这样我们就可以查看和打印它们。
    
    如果不使用 `list()` 函数，直接打印 `numbers_squared`，你会得到一个类似于以下输出的对象：
    
    ```
    <map object at 0x7f2e29eeedd0>
    ```
    
    这只是表示 `numbers_squared` 是一个 `map` 对象，而不是实际的结果列表。所以为了查看和使用结果，我们需要将其转换为列表形式。

**示例：2**

```py
numbers_str = ['1', '2', '3', '4', '5']  # 可迭代对象
numbers_int = map(int, numbers_str)
print(list(numbers_int))    # [1, 2, 3, 4, 5]
```

> `int()` 函数在 Python 中用于类型转换，将字符串转换为整数，或将其他数值类型（如浮点数）转换为整数

**示例：3**

```py
names = ['Asabeneh', 'Lidiya', 'Ermias', 'Abraham']  # 可迭代对象

def change_to_upper(name):
    return name.upper()

names_upper_cased = map(change_to_upper, names)
print(list(names_upper_cased))    # ['ASABENEH', 'LIDIYA', 'ERMIAS', 'ABRAHAM']

# 让我们使用lambda函数来应用它
names_upper_cased = map(lambda name: name.upper(), names)
print(list(names_upper_cased))    # ['ASABENEH', 'LIDIYA', 'ERMIAS', 'ABRAHAM']
```

实际上，map做的是对列表进行迭代。例如，它将名称更改为大写并返回一个新列表。

### Python - Filter函数

`filter()`函数调用指定函数，该函数为指定可迭代对象（列表）的每个项目返回布尔值。它会过滤满足过滤条件的项目。

```py
    # 语法
    filter(function, iterable)
```

**示例：1**

```py
# 让我们过滤出只有偶数的数字
numbers = [1, 2, 3, 4, 5]  # 可迭代对象

def is_even(num):
    if num % 2 == 0:
        return True
    return False

even_numbers = filter(is_even, numbers)
print(list(even_numbers))       # [2, 4]
```

**示例：2**

```py
numbers = [1, 2, 3, 4, 5]  # 可迭代对象

def is_odd(num):
    if num % 2 != 0:
        return True
    return False

odd_numbers = filter(is_odd, numbers)
print(list(odd_numbers))       # [1, 3, 5]
```

```py
# 过滤出长名称
names = ['Asabeneh', 'Lidiya', 'Ermias', 'Abraham']  # 可迭代对象
def is_name_long(name):
    if len(name) > 7:
        return True
    return False

long_names = filter(is_name_long, names)
print(list(long_names))         # ['Asabeneh']
```

### Python - Reduce函数

`reduce()`函数定义在`functools`模块中，我们应该从这个模块中导入它。与`map`和`filter`一样，它接受两个参数，一个函数和一个可迭代对象。但是，它不会返回另一个可迭代对象，而是返回一个**单一的值**。

**示例：1**

```py
from functools import reduce

numbers_str = ['1', '2', '3', '4', '5']  # 可迭代对象
def add_two_nums(x, y):
    return int(x) + int(y)

total = reduce(add_two_nums, numbers_str)
print(total)    # 15
```

!!! note "`reduce`执行过程"

    `reduce`是一个用于数据聚合的函数
    使用 `reduce` 函数进行累加操作：
    
     - `reduce` 函数接受两个参数，第一个参数是要应用于列表元素的函数，第二个参数是可迭代对象（在这里是 `numbers_str`）。
     - `reduce` 函数从可迭代对象中取出前两个元素，例如 '1' 和 '2'，然后将它们作为参数传递给 `add_two_nums` 函数，并执行相加操作，得到中间结果 `3`。
     - 然后，`reduce` 函数再次从可迭代对象中取出下一个元素 '3' 和上一次的中间结果 `3`，将它们传递给 `add_two_nums` 函数，执行相加操作，得到新的中间结果 `6`。
     - 这个过程继续，直到遍历完整个可迭代对象，得到最终的聚合结果 `15`。

## 💻 练习：第14天

```py
countries = ['Estonia', 'Finland', 'Sweden', 'Denmark', 'Norway', 'Iceland']
names = ['Asabeneh', 'Lidiya', 'Ermias', 'Abraham']
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

### 练习：级别1

1. 解释map、filter和reduce之间的区别。
2. 解释高阶函数、闭包和装饰器之间的区别。
3. 在map、filter或reduce之前定义一个调用函数，看看示例。
4. 使用for循环打印国家列表中的每个国家。
5. 使用for循环打印名称列表中的每个名称。
6. 使用for循环打印数字列表中的每个数字。

### 练习：级别2

1. 使用map创建一个新列表，将国家列表中的每个国家更改为大写。
2. 使用map创建一个新列表，将数字列表中的每个数字更改为其平方。
3. 使用map将名称列表中的每个名称更改为大写。
4. 使用filter过滤掉包含'land'的国家。
5. 使用filter过滤掉恰好有六个字符的国家。
6. 使用filter过滤掉包含六个字母或更多字母的国家。
7. 使用filter过滤掉以'E'开头的国家。
8. 链接两个或更多的列表迭代器（例如arr.map(callback).filter(callback).reduce(callback)）。
9. 声明一个名为get_string_lists的函数，该函数接受一个列表作为参数，然后返回一个只包含字符串项目的列表。
10. 使用reduce来计算数字列表中所有数字的总和。
11. 使用reduce来连接所有国家，并生成以下句子：Estonia, Finland, Sweden, Denmark, Norway和Iceland都是北欧国家。
12. 声明一个名为categorize_countries的函数，该函数返回具有某些公共模式的国家列表（您可以在此存储库的data文件夹中的countries.js文件中找到国家列表（例如'land'、'ia'、'island'、'stan'）。
13. 创建一个函数，返回一个字典，其中键代表以该字母开头的国家名称的首字母，而值是以该字母开头的国家名称的数量。
14. 声明一个名为get_first_ten_countries的函数，它从countries.js列表中的data文件夹中获取前十个国家的列表。
15. 声明一个名为get_last_ten_countries的函数，该函数返回国家列表中的最后十个国家。

### 练习：级别3

1. 使用countries_data.py文件（https://github.com/Asabeneh/30-Days-Of-Python/blob/master/data/countries-data.py）并按照以下任务操作：
   - 按名称、首都、人口对国家进行排序
   - 按位置筛选出十种最常用的语言。
   - 筛选出十个人口最多的国家。