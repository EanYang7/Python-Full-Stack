# 10 循环

## 循环

生活充满了日常工作routines。在编程中，我们也经常执行重复的任务。为了处理重复的任务，编程语言使用循环。Python编程语言也提供了以下两种类型的循环：

1. while循环
2. for循环

### While循环

我们使用保留字 _while_ 来创建一个while循环。它用于重复执行一组语句，直到满足给定条件为止。当条件变为假时，循环后的代码行将继续执行。

```py
  # 语法
while 条件:
    代码放在这里
```

**示例：**

```py
count = 0
while count < 5:
    print(count)
    count = count + 1
#输出从0到4
```

在上面的while循环中，当count为5时，条件变为假。这时循环停止。
如果我们想要在条件不再为真时运行一段代码块，我们可以使用 _else_。

```py
  # 语法
while 条件:
    代码放在这里
else:
    代码放在这里
```

**示例：**

```py
count = 0
while count < 5:
    print(count)
    count = count + 1
else:
    print(count)
```

上面的循环条件在count为5时为假，循环停止，然后执行else语句。结果会打印出5。

### Break和Continue - 第1部分

- Break：当我们想要退出或停止循环时，使用break。

```py
# 语法
while 条件:
    代码放在这里
    if 另一个条件:
        break
```

**示例：**

```py
count = 0
while count < 5:
    print(count)
    count = count + 1
    if count == 3:
        break
```

上面的while循环仅打印0、1、2，但当它达到3时会停止。

- Continue：使用continue语句，我们可以跳过当前迭代，继续下一次迭代：

```py
  # 语法
while 条件:
    代码放在这里
    if 另一个条件:
        continue
```

**示例：**

```py
count = 0
while count < 5:
    if count == 3:
        count = count + 1
        continue
    print(count)
    count = count + 1
```

上面的while循环仅打印0、1、2和4（跳过3）。

### For循环

使用 _for_ 关键字创建for循环，与其他编程语言类似，但有一些语法差异。循环用于迭代序列（可以是列表、元组、字典、集合或字符串）。

- 带列表的for循环

```py
# 语法
for 迭代器 in 列表:
    代码放在这里
```

**示例：**

```py
numbers = [0, 1, 2, 3, 4, 5]
for number in numbers: # number是用来引用列表项的临时名称，只在这个循环内部有效
    print(number)       # 数字将逐行打印，从0到5
```

- 带字符串的for循环

```py
# 语法
for 迭代器 in 字符串:
    代码放在这里
```

**示例：**

```py
language = 'Python'
for letter in language:
    print(letter)


for i in range(len(language)):
    print(language[i])
```

- 带元组的for循环

```py
# 语法
for 迭代器 in 元组:
    代码放在这里
```

**示例：**

```py
numbers = (0, 1, 2, 3, 4, 5)
for number in numbers:
    print(number)
```

- 带字典的for循环
  遍历字典会得到字典的键。

```py
  # 语法
for 迭代器 in 字典:
    代码放在这里
```

**示例：**

```py
person = {
    'first_name':'Asabeneh',
    'last_name':'Yetayeh',
    'age':250,
    'country':'Finland',
    'is_marred':True,
    'skills':['JavaScript', 'React', 'Node', 'MongoDB', 'Python'],
    'address':{
        'street':'Space street',
        'zipcode':'02210'
    }
}
for key in person:
    print(key)

for key, value in person.items():
    print(key, value) # 这样我们可以打印出键和值
```

- 集合中的循环

```py
# 语法
for 迭代器 in 集合:
    代码放在这里
```

**示例：**

```py
it_companies = {'Facebook', 'Google', 'Microsoft', 'Apple', 'IBM', 'Oracle', 'Amazon'}
for company in it_companies:
    print(company)
```

### Break和Continue - 第2部分

简短的提醒：
> 当我们想要在循环完成之前停止循环时，使用break。

```py
# 语法
for 迭代器 in 序列:
    代码放在这里
    if 条件:
        break
```

**示例：**

```py
numbers = (0,1,2,3,4,5)
for number in numbers:
    print(number)
    if number == 3:
        break
```

在上面的示例中，当它达到3时，循环停止。

> 当我们想要在循环迭代中跳过某些步骤时，使用continue。

```py
  # 语法
for 迭代器 in 序列:
    代码放在这里
    if 条件:
        continue
```

**示例：**

```py
numbers = (0,1,2,3,4,5)
for number in numbers:
    print(number)
    if number == 3:
       continue
    print('下一个数字应该是', number + 1) if number != 5 else print("循环结束") # 对于简写条件需要同时使用if和else语句
print('循环外')
```

在上面的示例中，如果数字等于3，那么在条件后的步骤（但在循环内）会被跳过，如果还有其他迭代，循环继续执行。

### Range函数

_range()_ 函数用于生成一系列数字。_range(start, end, step)_ 接受三个参数：起始、结束和步进。默认情况下，它从0开始，步进为1。range序列至少需要一个参数（结束）。
使用range创建序列

```py
lst = list(range(11)) 
print(lst) # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
st = set(range(1, 11))    # 2个参数表示序列的起始和结束，步长设置为默认值1
print(st) # {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}

lst = list(range(0,11,2))
print(lst) # [0, 2, 4, 6, 8, 10]
st = set(range(0,11,2))
print(st) #  {0, 2, 4, 6, 8, 10}
```

```py
# 语法
for 迭代器 in range(起始, 结束, 步进):
```

**示例：**

```py
for number in range(11):
    print(number)   # 打印0到10，不包括11
```

### 嵌套的For循环

我们可以在循环内部编写循环。

```py
# 语法
for x in y:
    for t in x:
        print(t)
```

**示例：**

```py
person = {
    'first_name': 'Asabeneh',
    'last_name': 'Yetayeh',
    'age': 250,
    'country': 'Finland',
    'is_marred': True,
    'skills': ['JavaScript', 'React', 'Node', 'MongoDB', 'Python'],
    'address': {
        'street': 'Space street',
        'zipcode': '02210'
    }
}
for key in person:
    if key == 'skills':
        for skill in person['skills']:
            print(skill)
```

### For Else

如果我们想在循环结束时执行一些消息，我们可以使用else。

```py
# 语法
for 迭代器 in range(起始, 结束, 步进):
    做某事
else:
    print('循环结束')
```

**示例：**

```py
for number in range(11):
    print(number)   # 打印0到10，不包括11
else:
    print('循环停在', number)
```

### Pass

在Python中，当需要语句（分号后）但我们不想执行任何代码时，我们可以写上单词 _pass_ 来避免错误。同时，我们可以将其用作未来语句的占位符。

**示例：**

```py
for number in range(6):
    pass
```

## 💻 练习：第10天

### 练习：级别1

1. 使用for循环迭代0到10，然后使用while循环执行相同的操作。

2. 使用for循环迭代10到0，然后使用while循环执行相同的操作。

3. 编写一个循环，调用七次print()，以便我们在输出中获得以下三角形：

   ```py
     #
     ##
     ###
     ####
     #####
     ######
     #######
   ```

4. 使用嵌套循环创建以下内容：

   ```sh
   # # # # # # # #
   # # # # # # # #
   # # # # # # # #
   # # # # # # # #
   # # # # # # # #
   # # # # # # # #
   # # # # # # # #
   # # # # # # # #
   ```

5. 打印以下模式：

   ```sh
   0 x 0 = 0
   1 x 1 = 1
   2 x 2 = 4
   3 x 3 = 9
   4 x 4 = 16
   5 x 5 = 25
   6 x 6 = 36
   7 x 7 = 49
   8 x 8 = 64
   9 x 9 = 81
   10 x 10 = 100
   ```

6. 使用for循环迭代列表['Python', 'Numpy','Pandas','Django', 'Flask']，并打印出其中的项。

7. 使用for循环迭代0到100，仅打印偶数。

8. 使用for循环迭代0到100，仅打印奇数。

### 练习：级别2

1. 使用for循环迭代0到100，并打印所有数字的和。

   ```sh
   所有数字的总和是5050。
   ```

2. 使用for循环迭代0到100，并打印所有偶数的和以及所有奇数的和。

   ```sh
   所有偶数的总和为2550。而所有奇数的总和为2500。
   ```

### 练习：级别3

1. 进入data文件夹，使用[countries.py](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/data/countries.py)文件。循环遍历国家并提取所有包含单词 _land_ 的国家。
2. 这是一个水果列表，['banana', 'orange', 'mango', 'lemon'] 使用循环反转顺序。
3. 进入data文件夹，使用[countries_data.py](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/data/countries-data.py)文件。
   1. 数据中有多少种语言
   2. 从数据中找出使用最多的十种语言
   3. 找出世界上人口最多的10个国家
