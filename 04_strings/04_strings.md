# 04 字符串

文本是一种字符串数据类型。任何以文本形式编写的数据类型都是字符串。任何在单引号、双引号或三重引号下的数据都是字符串。有不同的字符串方法和内置函数来处理字符串数据类型。要检查字符串的长度，请使用`len()`方法。

## 创建字符串

```python
letter = 'P'                # 一个字符串可以是一个单字符或一堆文本
print(letter)               # P
print(len(letter))          # 1
greeting = 'Hello, World!'  # 字符串可以使用单引号或双引号创建，"Hello, World!"
print(greeting)             # Hello, World!
print(len(greeting))        # 13
sentence = "I hope you are enjoying 30 days of Python Challenge"
print(sentence)
```

多行字符串可以使用三重单引号`''''`或三重双引号`""""`创建。请参考以下示例。

```python
multiline_string = '''I am a teacher and enjoy teaching.
I didn't find anything as rewarding as empowering people.
That is why I created 30 days of python.'''
print(multiline_string)

# 还有另一种做同样事情的方法
multiline_string = """I am a teacher and enjoy teaching.
I didn't find anything as rewarding as empowering people.
That is why I created 30 days of python."""
print(multiline_string)
```

## 字符串连接

我们可以将字符串连接在一起。合并或连接字符串称为字符串连接。请参考以下示例：

```python
first_name = 'Asabeneh'
last_name = 'Yetayeh'
space = ' '
full_name = first_name  +  space + last_name
print(full_name) # Asabeneh Yetayeh
# 使用len()内置函数检查字符串的长度
print(len(first_name))  # 8
print(len(last_name))   # 7
print(len(first_name) > len(last_name)) # True
print(len(full_name)) # 16
```

## 字符串中的转义序列

在Python和其他编程语言中，`\`后面跟着一个字符是转义序列。让我们看看最常见的转义字符：

- `\n`：换行
- `\t`：制表符（相当于8个空格）
- `\`：反斜杠
- `\'`：单引号`’`
- `\\"`：双引号`"`

现在，让我们使用示例来了解上述转义序列的用法。

```python
print('I hope everyone is enjoying the Python Challenge.\nAre you ?') # 换行
print('Days\tTopics\tExercises') # 添加制表符或4个空格
print('Day 1\t5\t5')
print('Day 2\t6\t20')
print('Day 3\t5\t23')
print('Day 4\t1\t35')
print('This is a backslash  symbol (\\)') # 写一个反斜杠
print('In every programming language it starts with \"Hello, World!\"') # 在单引号内写双引号

# 输出
I hope every one is enjoying the Python Challenge.
Are you ?
Days	Topics	Exercises
Day 1	5	    5
Day 2	6	    20
Day 3	5	    23
Day 4	1	    35
This is a backslash  symbol (\)
In every programming language it starts with "Hello, World!"
```

## 字符串格式化

### 旧式字符串格式化（%运算符）

在Python中，有许多格式化字符串的方式。在本节中，我们将介绍其中一些。
`%`运算符用于格式化一组变量，这些变量包含在一个“元组”（固定大小的列表）中，与格式化字符串一起使用，格式化字符串中包含常规文本和“参数说明符”等特殊符号，如`%s`，`%d`，`%f`，`%.<小数位数> f`。

- `%s` - 字符串（或具有字符串表示的任何对象，如数字）
- `%d` - 整数
- `%f` - 浮点数
- `%.<小数位数>f` - 具有固定精度的浮点数

```python
# 仅包含字符串
first_name = 'Asabeneh'
last_name = 'Yetayeh'
language = 'Python'
formated_string = 'I am %s %s. I teach %s' %(first_name, last_name, language)
print(formated_string)

# 包含字符串和数字
radius = 10
pi = 3.14
area = pi * radius ** 2
formated_string = 'The area of circle with a radius %d is %.2f.' %(radius, area) # 2表示小数点后的2个有效数字
python_libraries = ['Django', 'Flask', 'NumPy', 'Matplotlib','Pandas']
formated_string = 'The following are python libraries:%s' % (python_libraries)
print(formated_string) # "The following are python libraries:['Django', 'Flask', 'NumPy', 'Matplotlib','Pandas']"
```

### 新式字符串格式化（str.format）

这种格式化是在Python 3版中引入的。

```python
first_name = 'Asabeneh'
last_name = 'Yetayeh'
language = 'Python'
formated_string = 'I am {} {}. I teach {}'.format(first_name, last_name, language)
print(formated_string)
a = 4
b = 3
print('{} + {} = {}'.format(a, b, a + b))
print('{} - {} = {}'.format(a, b, a - b))
print('{} * {} = {}'.format(a, b, a * b))
print('{} / {} = {:.2f}'.format(a, b, a / b)) # 限制小数点后两位
print('{} % {} = {}'.format(a, b, a % b))
print('{} // {} = {}'.format(a, b, a // b))
print('{} ** {} = {}'.format(a, b, a ** b))

# 输出
4 + 3 = 7
4 - 3 = 1
4 * 3 = 12
4 / 3 = 1.33
4 % 3 = 1
4 // 3 = 1
4 ** 3 = 64

# 字符串和数字
radius = 10
pi = 3.14
area = pi * radius ** 2
formated_string = 'The area of a circle with a radius {} is {:.2f}.'.format(radius, area) # 2位

小数
print(formated_string)
```

### 字符串插值 / f-Strings（Python 3.6+）

另一种新的字符串格式化是字符串插值，即f-字符串。字符串以f开头，我们可以在相应的位置注入数据。

```python
a = 4
b = 3
print(f'{a} + {b} = {a +b}')
print(f'{a} - {b} = {a - b}')
print(f'{a} * {b} = {a * b}')
print(f'{a} / {b} = {a / b:.2f}')
print(f'{a} % {b} = {a % b}')
print(f'{a} // {b} = {a // b}')
print(f'{a} ** {b} = {a ** b}')
```

## Python字符串作为字符序列

Python字符串是字符序列，与其他Python有序对象的基本访问方法相同——列表和元组。从字符串中提取单个字符的最简单方法（以及从任何序列中提取单个成员）是将它们解包到相应的变量中。

### 解包字符

```python
language = 'Python'
a,b,c,d,e,f = language # 解包序列字符到变量
print(a) # P
print(b) # y
print(c) # t
print(d) # h
print(e) # o
print(f) # n
```

### 通过索引访问字符串中的字符

在编程中，从零开始计数。因此，字符串的第一个字母位于零索引处，字符串的最后一个字母是字符串长度减1。

### 切片Python字符串

在python中，我们可以将字符串切片成子字符串。

```python
language = 'Python'
first_three = language[0:3] # 从零索引开始，直到3，但不包括3
print(first_three) #Pyt
last_three = language[3:6]
print(last_three) # hon
# 另一种方法
last_three = language[-3:]
print(last_three)   # hon
last_three = language[3:]
print(last_three)   # hon
```

### 反转字符串

我们可以轻松地反转字符串。

```python
greeting = 'Hello, World!'
print(greeting[::-1]) # !dlroW ,olleH
```

### 在切片时跳过字符

在切片时，可以通过将步骤参数传递给切片方法来跳过字符。

```python
language = 'Python'
pto = language[0:6:2] #
print(pto) # Pto
```

## 字符串方法

有许多字符串方法允许我们格式化字符串。请参考以下示例中的一些字符串方法：

- `capitalize()`: 将字符串的第一个字符转换为大写字母

```python
challenge = 'thirty days of python'
print(challenge.capitalize()) # 'Thirty days of python'
```

- `count()`: 返回字符串中子字符串的出现次数，`count(substring, start=.., end=..)`。`start`是计数的起始索引，`end`是计数的最后一个索引。

```python
challenge = 'thirty days of python'
print(challenge.count('y')) # 3
print(challenge.count('y', 7, 14)) # 1
print(challenge.count('th')) # 2
```

- `endswith()`: 检查字符串是否以指定的后缀结束

```python
challenge = 'thirty days of python'
print(challenge.endswith('on'))   # True
print(challenge.endswith('tion')) # False
```

- `expandtabs()`: 用空格替换制表符字符，默认制表符大小为8。它接受制表符大小参数。

```python
challenge = 'thirty\tdays\tof\tpython'
print(challenge.expandtabs())   # 'thirty  days    of      python'
print(challenge.expandtabs(10)) # 'thirty    days      of        python'
```

- `find()`: 返回子字符串的第一次出现的索引，如果未找到则返回-1

```python
challenge = 'thirty days of python'
print(challenge.find('y'))  # 5
print(challenge.find('th')) # 0
```

- `rfind()`: 返回子字符串的最后一次出现的索引，如果未找到则返回-1

```python
challenge = 'thirty days of python'
print(challenge.rfind('y'))  # 16
print(challenge.rfind('th')) # 17
```

- `format()`: 将字符串格式化为更好的输出。
  有关字符串格式化的更多信息，请查看[此链接](https://www.programiz.com/python-programming/methods/string/format)

```python
first_name = 'Asabeneh'
last_name = 'Yetayeh'
age = 250
job = 'teacher'
country = 'Finland'
sentence = 'I am {} {}. I am a {}. I am {} years old. I live in {}.'.format(first_name, last_name, age, job, country)
print(sentence) # I am Asabeneh Yetayeh. I am 250 years old. I am a teacher. I live in Finland.

radius = 10
pi = 3.14
area = pi * radius ** 2
result = 'The area of a circle with radius {} is {}'.format(str(radius), str(area))
print(result) # The area of a circle with radius 10 is 314
```

- `index()`: 返回子字符串的最低索引，附加参数指示开始和结束索引（默认为0和字符串长度-1）。如果未找到子字符串，则引发ValueError。

```python
challenge = 'thirty days of python'
sub_string = 'da'
print(challenge.index(sub_string))  # 7
print(challenge.index(sub_string, 9)) # 错误
```

- `rindex()`: 返回子字符串的最高索引，附加参数指示开始和结束索引（默认为0和字符串长度-1）。

```python
challenge = 'thirty days of python'
sub_string = 'da'
print(challenge.rindex(sub_string))  # 8
print(challenge.rindex(sub_string, 9)) # 错误
```

- `isalnum()`: 检查是否为字母数字字符

```python
challenge = 'ThirtyDaysPython'
print(challenge.isalnum()) # True

challenge = '30DaysPython'
print(challenge.isalnum()) # True

challenge = 'thirty days of python'
print(challenge.isalnum()) # False，空格不是字母数字字符

challenge = 'thirty days of python 2019'
print(challenge.isalnum()) # False
```

- `isalpha()`: 检查字符串中的所有元素是否都是字母字符（a-z和A-Z）

```python
challenge = 'thirty days of python'
print(challenge.isalpha()) # False，空格再次被排除
challenge = 'ThirtyDaysPython'
print(challenge.isalpha()) # True
num = '123'
print(num.isalpha())      # False
```

- `isdecimal()`: 检查字符串中的所有字符是否都是十进制数字（0-9）

```python
challenge = 'thirty days of python'
print(challenge.isdecimal())  # False
challenge = '123'
print(challenge.isdecimal())  # True
challenge = '\u00B2'
print(challenge.isdigit())   # False
challenge = '12 3'
print(challenge.isdecimal())  # False，不允许空格
```

- `isdigit()`: 检查字符串中的所有字符是否都是数字（0-9和一些其他用于表示数字的Unicode字符）

```python
challenge = 'Thirty'
print(challenge.isdigit()) # False
challenge = '30'
print(challenge.isdigit())   # True
challenge = '\u00B2'
print(challenge.isdigit())   # True
```

- `isnumeric()`: 检查字符串中的所有字符是否都是数字或与数字有关（与`isdigit()`相似，只接受更多的符号，如½）

```python
num = '10'
print(num.isnumeric()) # True
num = '\u00BD' # ½
print(num.isnumeric()) # True
num = '10.5'
print(num.isnumeric()) # False
```

- `isidentifier()`: 检查是否为有效标识符 - 它检查字符串是否为有效的变量名

```python
challenge = '30DaysOfPython'
print(challenge.isidentifier()) # False，因为以数字开头
challenge = 'thirty_days_of_python'
print(challenge.isidentifier()) # True
```

- `islower()`: 检查字符串中的所有字母字符是否都是小写

```python
challenge = 'thirty days of python'
print(challenge.islower()) # True
challenge = 'Thirty days of python'
print(challenge.islower()) # False
```

- `isupper()`: 检查字符串中的所有字母字符是否都是大写

```python
challenge = 'thirty days of python'
print(challenge.isupper()) # False
challenge = 'THIRTY DAYS OF PYTHON'
print(challenge.isupper()) # True
```

- `join()`: 返回连接的字符串

```python
web_tech = ['HTML', 'CSS', 'JavaScript', 'React']
result = ' '.join(web_tech)
print(result) # 'HTML CSS JavaScript React'
```

```python
web_tech = ['HTML', 'CSS', 'JavaScript', 'React']
result = '# '.join(web_tech)
print(result) # 'HTML# CSS# JavaScript# React'
```

- `strip()`: 从字符串的开头和结尾删除所有给定的字符

> 注意是满足条件的单个字符，不是字符串

```python
challenge = 'thirty days of pythoonnn'
print(challenge.strip('noth')) # 'irty days of py'
```

- `replace()`: 用给定的字符串替换子字符串

```python
challenge = 'thirty days of python'
print(challenge.replace('python', 'coding')) # 'thirty days of coding'
```

- `split()`: 使用给定的字符串或空格作为分隔符拆分字符串

```python
challenge = 'thirty days of python'
print(challenge.split()) # ['thirty', 'days', 'of', 'python']
challenge = 'thirty, days, of, python'
print(challenge.split(', ')) # ['thirty', 'days', 'of', 'python']
```

- `title()`: 返回以标题格式的字符串

```python
challenge = 'thirty days of python'
print(challenge.title()) # Thirty Days Of Python
```

- `swapcase()`: 将所有大写字符转换为小写字符，将所有小写字符转换为大写字符

```python
challenge = 'thirty days of python'
print(challenge.swapcase())   # THIRTY DAYS OF PYTHON
challenge = 'Thirty Days Of Python'
print(challenge.swapcase())  # tHIRTY dAYS oF pYTHON
```

- `startswith()`: 检查字符串是否以指定的字符串开头

```python
challenge = 'thirty days of python'
print(challenge.startswith('thirty')) # True

challenge = '30 days of python'
print(challenge.startswith('thirty')) # False
```

🌕 你是一个非凡的人，拥有卓越的潜力。 你刚刚完成了第4天的挑战，你已经走在了伟大之路上的四步。 现在，为你的大脑和肌肉做一些练习。

## 💻 练习

1. 将字符串 'Thirty', 'Days', 'Of', 'Python' 连接为一个单一的字符串 'Thirty Days Of Python'。

2. 将字符串 'Coding', 'For', 'All' 连接为一个单一的字符串 'Coding For All'。

3. 声明一个名为 `company` 的变量，并将其初始值设置为 "Coding For All"。

4. 使用 `print()` 打印变量 `company`。

5. 使用 `len()` 方法打印字符串 `company` 的长度，并使用 `print()` 打印结果。

6. 使用 `upper()` 方法将所有字符更改为大写字母。

7. 使用 `lower()` 方法将所有字符更改为小写字母。

8. 使用 `capitalize()`、`title()` 和 `swapcase()` 方法格式化字符串值 "Coding For All"。

9. 切割出 "Coding For All" 字符串的第一个单词。

10. 检查 "Coding For All" 字符串是否包含单词 "Coding"，使用 `index()`、`find()` 或其他方法。

11. 将字符串 "Coding For All" 中的单词 "Coding" 替换为 "Python"。

12. 使用替换方法或其他方法将 "Python for Everyone" 更改为

 "Python for All"。

13. 使用空格作为分隔符（`split()`）拆分字符串 "Coding For All"。

14. 请将字符串 "Facebook, Google, Microsoft, Apple, IBM, Oracle, Amazon" 以逗号分隔拆分。

15. 字符串 "Coding For All" 中索引为0的字符是什么？

16. 字符串 "Coding For All" 中的最后一个索引是什么？

17. 在字符串 "Coding For All" 中的索引10处是什么字符？

18. 为名称 'Python For Everyone' 创建一个首字母缩写或简称。

19. 为名称 'Coding For All' 创建一个首字母缩写或简称。

20. 使用 `index()` 确定字符串 "Coding For All" 中C的第一次出现的位置。

21. 使用 `index()` 确定字符串 "Coding For All" 中F的第一次出现的位置。

22. 使用 `rfind()` 确定字符串 "Coding For All People" 中l的最后一次出现的位置。

23. 使用 `index()` 或 `find()` 查找以下句子中单词 'because' 的第一次出现位置：'You cannot end a sentence with because because because is a conjunction'。

24. 使用 `rindex()` 查找以下句子中单词 'because' 的最后一次出现位置：'You cannot end a sentence with because because because is a conjunction'。

25. 在以下句子中切割出短语 'because because because'：'You cannot end a sentence with because because because is a conjunction'。

26. 在以下句子中找到单词 'because' 的第一次出现的位置：'You cannot end a sentence with because because because is a conjunction'。

27. 在以下句子中切割出短语 'because because because'：'You cannot end a sentence with because because because is a conjunction'。

28. 字符串 '\Coding For All' 是否以子串 'Coding' 开头？

29. 字符串 'Coding For All' 是否以子串 'coding' 结尾？

30. '&nbsp;&nbsp; Coding For All &nbsp;&nbsp;&nbsp; &nbsp;' &nbsp;，移除给定字符串的左侧和右侧的空格。

31. 以下哪个变量在使用 `isidentifier()` 方法时返回 True：

    - 30DaysOfPython
    - thirty_days_of_python

32. 以下列表包含一些Python库的名称：['Django', 'Flask', 'Bottle', 'Pyramid', 'Falcon']。使用空格字符串作为分隔符，将列表连接起来。

33. 使用新行转义序列分隔以下句子。

    ```python
    I am enjoying this challenge.
    I just wonder what is next.
    ```

34. 使用制表符转义序列编写以下行。

    ```python
    Name      Age     Country   City
    Asabeneh  250     Finland   Helsinki
    ```

35. 使用字符串格式化方法显示以下内容：

```sh
radius = 10
area = 3.14 * radius ** 2
The area of a circle with radius 10 is 314 meters square.
```

36. 使用字符串格式化方法制作以下内容：

```sh
8 + 6 = 14
8 - 6 = 2
8 * 6 = 48
8 / 6 = 1.33
8 % 6 = 2
8 // 6 = 1
8 ** 6 = 262144
```
