# 12 模块

## 模块

### 什么是模块

一个模块是一个包含一组代码或一组函数的文件，可以包含到一个应用程序中。一个模块可以是包含单个变量、函数或大型代码库的文件。

### 创建模块

要创建一个模块，我们需要在Python脚本中编写代码，然后将其保存为一个.py文件。在项目文件夹中创建一个名为mymodule.py的文件。让我们在这个文件中写一些代码。

```py
# mymodule.py文件
def generate_full_name(firstname, lastname):
    return firstname + ' ' + lastname
```

在项目目录中创建main.py文件，并导入mymodule.py文件。

### 导入模块

要导入文件，我们使用_import_关键字和文件的名称。

```py
# main.py文件
import mymodule
print(mymodule.generate_full_name('Asabeneh', 'Yetayeh')) # Asabeneh Yetayeh
```

### 从模块导入函数

我们可以在一个文件中有很多函数，并且我们可以分别导入所有这些函数。

```py
# main.py文件
from mymodule import generate_full_name, sum_two_nums, person, gravity
print(generate_full_name('Asabneh', 'Yetayeh'))
print(sum_two_nums(1,9))
mass = 100;
weight = mass * gravity
print(weight)
print(person['firstname'])
```

### 从模块导入函数并重命名

在导入时，我们可以重命名模块的名称。

```py
# main.py文件
from mymodule import generate_full_name as fullname, sum_two_nums as total, person as p, gravity as g
print(fullname('Asabneh', 'Yetayeh'))
print(total(1, 9))
mass = 100;
weight = mass * g
print(weight)
print(p)
print(p['firstname'])
```

## 导入内置模块

与其他编程语言一样，我们也可以通过使用关键字`import`来导入文件/函数。让我们导入大多数时间都会使用的常见模块。一些常见的内置模块有：_math_，_datetime_，_os_，_sys_，_random_，_statistics_，_collections_，_json_，_re_

### OS模块

使用Python的 `os` 模块，可以自动执行许多操作系统任务。Python中的OS模块提供了用于创建、更改当前工作目录和删除目录（文件夹）、获取其内容、更改和标识当前目录的函数。

```py
# 导入模块
import os
# 创建目录
os.mkdir('目录名')
# 更改当前目录
os.chdir('路径')
# 获取当前工作目录
os.getcwd()
# 删除目录
os.rmdir()
```

### Sys模块

sys模块提供了用于操作Python运行时环境的不同部分的函数和变量。sys.argv函数返回传递给Python脚本的命令行参数的列表。此列表中的索引0始终是脚本的名称，索引1是从命令行传递的参数。

示例脚本.py文件：

```py
import sys
#print(sys.argv[0], argv[1],sys.argv[2])  # 此行将打印出：文件名 参数1 参数2
print('欢迎 {}. 享受 {} 挑战！'.format(sys.argv[1], sys.argv[2]))
```

现在，为了检查这个脚本的工作原理，我在命令行中输入了以下内容：

```sh
python script.py Asabeneh 30DaysOfPython
```

结果：

```sh
欢迎 Asabeneh. 享受 30DayOfPython 挑战！
```

一些有用的sys命令：

```py
# 退出sys
sys.exit()
# 可以接受的最大整数变量
sys.maxsize
# 环境路径
sys.path
# 使用的Python版本
sys.version
```

### Statistics模块

statistics模块提供了用于数值数据的数学统计的函数。在此模块中定义的一些常见统计函数包括：_mean_，_median_，_mode_，_stdev_ 等。

```py
from statistics import * # 导入所有统计模块
ages = [20, 20, 4, 24, 25, 22, 26, 20, 23, 22, 26]
print(mean(ages))       # ~22.9
print(median(ages))     # 23
print(mode(ages))       # 20
print(stdev(ages))      # ~2.3
```

### 数学模块

包含许多数学操作和常量的模块。

```py
import math
print(math.pi)           # 3.141592653589793，圆周率
print(math.sqrt(2))      # 1.4142135623730951，平方根
print(math.pow(2, 3))    # 8.0，指数函数
print(math.floor(9.81))  # 9，向下取整
print(math.ceil(9.81))   # 10，向上取整
print(math.log10(100))   # 2，以10为底的对数
```

现在，我们已经导入了 *math* 模块，该模块包含许多可帮助我们执行数学计算的函数。要检查模块具有哪些函数，我们可以使用 _help(math)_ 或 _dir(math)_。这将显示模块中可用的函数。如果我们只想从模块中导入特定的函数，可以按如下方式导入：

```py
from math import pi
print(pi)
```

还可以一次导入多个函数

```py
from math import pi, sqrt, pow, floor, ceil, log10
print(pi)                 # 3.141592653589793
print(sqrt(2))            # 1.4142135623730951
print(pow(2, 3))          # 8.0
print(floor(9.81))        # 9
print(ceil(9.81))         # 10
print(math.log10(100))    # 2

```

但如果我们想导入数学模块中的所有函数，可以使用 \* 。

```py
from math import *
print(pi)                  # 3.141592653589793，圆周率
print(sqrt(2))             # 1.4142135623730951，平方根
print(pow(2, 3))           # 8.0，指数
print(floor(9.81))         # 9，向下取整
print(ceil(9.81))          # 10，向上取整
print(math.log10(100))     # 2
```

当我们导入时，还可以重新命名函数的名称。

```py
from math import pi as  PI
print(PI) # 3.141592653589793
```

### 字符串模块

字符串模块是一个用途广泛的模块。下面的示例展示了字符串模块的一些用法。

```py
import string
print(string.ascii_letters) # abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ
print(string.digits)        # 0123456789
print(string.punctuation)   # !"#$%&'()*+,-./:;<=>?@[\]^_`{|}~
```

### 随机模块

到目前为止，您已经熟悉了如何导入模块。让我们再次导入 _random_ 模块，该模块会给我们生成一个在0和0.9999之间的随机数。_random_ 模块有许多函数，但在本节中，我们只会使用 _random_ 和 _randint_。

```py
from random import random, randint
print(random())   # 它不接受任何参数；返回一个在0和0.9999之间的值
print(randint(5, 20)) # 返回一个介于[5, 20]的随机整数
```

## 💻 练习：第12天

### 练习：级别1

1. 编写一个函数，生成一个六位/字符的随机用户ID。

   ```py
     print(random_user_id());
     '1ee33d'
   ```

2. 修改上一个任务。声明一个名为 user_id_gen_by_user 的函数。它不接受任何参数，但使用 input() 获取两个输入。一个输入是字符数，另一个输入是要生成的用户ID的数量。

```py
print(user_id_gen_by_user()) # 用户输入: 5 5
# 输出:
# kcsy2
# SMFYb
# bWmeq
# ZXOYh
# 2Rgxf
   
print(user_id_gen_by_user()) # 用户输入: 16 5
# 1GCSgPLMaBAVQZ26
# YD7eFwNQKNs7qXaT
# ycArC5yrRupyG00S
# UbGxOFI7UXSWAyKN
# dIV0SSUTgAdKwStr
```

3. 编写一个名为 rgb_color_gen 的函数。它将生成RGB颜色（每个值在0到255之间）。

```py
print(rgb_color_gen())
# rgb(125,244,255) - 输出应该采用这种格式
```

### 练习：级别2

1. 编写一个名为 list_of_hexa_colors 的函数，它在数组中返回任意数量的十六进制颜色（#后面写有六个十六进制数字。十六进制数字系统由16个符号组成，0-9和字母a-f。查看任务6以获取输出示例）。
1. 编写一个名为 list_of_rgb_colors 的函数，它在数组中返回任意数量的RGB颜色。
1. 编写一个名为 generate_colors 的函数，它可以生成任意数量的十六进制或RGB颜色。

```py
generate_colors('hexa', 3) # ['#a3e12f','#03ed55','#eb3d2b'] 
generate_colors('hexa', 1) # ['#b334ef']
generate_colors('rgb', 3)  # ['rgb(5, 55, 175','rgb(50, 105, 100','rgb(15, 26, 80'] 
generate_colors('rgb', 1)  # ['rgb(33,79, 176)']
```

### 练习：级别3

1. 调用你的 shuffle_list 函数，它接受一个列表作为参数，并返回一个打乱的列表。
1. 编写一个函数，它返回一个在0-9范围内的七个随机数的数组。所有的数字必须是唯一的。
