# 18 正则表达式

## 正则表达式

正则表达式（regular expression或者RegEx）是一种特殊的文本字符串，用于在数据中查找模式patterns。正则表达式可以用于检查不同数据类型中是否存在某种模式。要在Python中使用正则表达式，首先我们应该导入称为*re*的正则表达式模块。

### *re*模块

导入模块后，我们可以使用它来检测或查找模式。

```py
import re
```

### *re*模块中的方法

要查找模式，我们使用不同的*re*字符集，允许在字符串中搜索匹配项。

- *re.match()*：仅在字符串的第一行开头搜索，并返回匹配的对象（如果找到），否则返回None。
- *re.search*：如果在字符串中的任何位置都有匹配对象，则返回匹配对象，包括多行字符串。
- *re.findall*：返回包含所有匹配项的列表
- *re.split*：获取字符串，将其分割为匹配点，并返回列表
- *re.sub*：替换字符串中的一个或多个匹配项

#### 匹配

```py
# 语法
re.match(substring, string, re.I)
# substring是一个字符串或模式，string是我们要查找模式的文本，re.I是不区分大小写
```

>`re.I` 是 Python 中 `re`（正则表达式）模块的一个常量，代表 "IGNORECASE"。当你在使用正则表达式进行模式匹配时，加上 `re.I` 会让匹配操作忽略大小写。这意味着，无论是大写还是小写的字符都会被视为等效。

```py
import re

txt = 'I love to teach python and javaScript'
# 它返回一个具有span和match的对象
match = re.match('I love to teach', txt, re.I)
print(match)  # <re.Match object; span=(0, 15), match='I love to teach'>
# 我们可以使用span作为元组获取匹配的起始和结束位置
span = match.span()
print(span)     # (0, 15)
# 让我们从span中找到开始和结束位置
start, end = span
print(start, end)  # 0, 15
substring = txt[start:end]
print(substring)       # I love to teach
```

正如您从上面的示例中看到的，我们正在寻找的模式（或我们正在寻找的子字符串）是*I love to teach*。只有在文本以该模式开头时，匹配函数才会返回一个对象。

```py

txt = 'I love to teach python and javaScript'
match = re.match('I like to teach', txt, re.I)
print(match)  # None

```

字符串不以*I like to teach*开头，因此没有匹配，匹配方法返回None。

#### 搜索

```py
# 语法
re.match(substring, string, re.I)
# substring是一个模式，string是我们要查找模式的文本，re.I是不区分大小写标志
```

```py
import re

txt = '''Python is the most beautiful language that a human being has ever created.
I recommend python for a first programming language'''

# 它返回一个具有span和match的对象
match = re.search('first', txt, re.I)
print(match)  # <re.Match object; span=(100, 105), match='first'>
# 我们可以使用span作为元组获取匹配的起始和结束位置
span = match.span()
print(span)     # (100, 105)
# 让我们从span中找到开始和停止位置
start, end = span
print(start, end)  # 100 105
substring = txt[start:end]
print(substring)       # first
```

如您所见，search比match更好，因为它可以在整个文本中查找模式。搜索返回一个匹配对象，其中包含找到的第一个匹配项，否则它将返回*None*。一个更好的*re*函数是*findall*。此函数检查整个字符串的模式并将所有匹配项作为列表返回。

#### 使用*findall*查找所有匹配项

*findall()*返回所有匹配项的列表

```py
txt = '''Python is the most beautiful language that a human being has ever created.
I recommend python for a first programming language'''

# 它返回一个列表
matches = re.findall('language', txt, re.I)
print(matches)  # ['language', 'language']
```

如您所见，字符串*language*在字符串中出现了两次。现在我们来练习一下。
现在，我们将在字符串中查找Python和python两个单词：

```py
txt = '''Python is the most beautiful language that a human being has ever created.
I recommend python for a first programming language'''

# 它返回一个列表
matches = re.findall('python', txt, re.I)
print(matches)  # ['Python', 'python']

```

由于我们使用了*re.I*，因此包括了大写和小写字母。如果没有re.I标志，那么我们将不得不以不同的方式编写模式。让我们来看看：

```py
txt = '''Python is the most beautiful language that a human being has ever created.
I recommend python for a first programming language'''

matches = re.findall('Python|python', txt)
print(matches)  # ['Python', 'python']

#
matches = re.findall('[Pp]ython', txt)
print(matches)  # ['Python', 'python']

```

>在正则表达式中：
>
>1. `'Python|python'` 表示匹配字符串 "Python" 或 "python"。符号 `|` 在正则表达式中用作“或”运算符，意味着它会匹配在 `|` 符号前或后的任何一个模式。所以这个表达式会匹配 "Python" 和 "python" 这两个不同的字符串。
>2. `'[Pp]ython'` 是一个稍微不同的表达式。在正则表达式中，方括号 `[]` 用来表示一个字符集。在这个特定的字符集 `[Pp]` 中，它表示匹配大写 "P" 或小写 "p"。因此，这个表达式会匹配以 "P" 或 "p" 开始，后面跟着 "ython" 的任何字符串，这意味着它也会匹配 "Python" 和 "python"。
>
>虽然这两个表达式的写法不同，但它们都能匹配文本中的 "Python" 和 "python"。

#### 替换子字符串

```py
txt = '''Python is the most beautiful language that a human being has ever created.
I recommend python for a first programming language'''

match_replaced = re.sub('Python|python', 'JavaScript', txt, re.I)
print(match_replaced)  # JavaScript is the most beautiful language that a human being has ever created.
# OR
match_replaced = re.sub('[Pp]ython', 'JavaScript', txt, re.I)
print(match_replaced)  # JavaScript is the most beautiful language that a human being has ever created.
```

让我们再添加一个示例。以下字符串非常难以阅读，除非我们删除%符号。用

空字符串替换%将清除文本。

```py
txt = '''%I a%m te%%a%%che%r% a%n%d %% I l%o%ve te%ach%ing. 
T%he%re i%s n%o%th%ing as r%ewarding a%s e%duc%at%i%ng a%n%d e%m%p%ow%er%ing p%e%o%ple.
I fo%und te%a%ching m%ore i%n%t%er%%es%ting t%h%an any other %jobs. 
D%o%es thi%s m%ot%iv%a%te %y%o%u to b%e a t%e%a%cher?'''

matches = re.sub('%', '', txt)
print(matches)
```

```sh
I am teacher and I love teaching.
There is nothing as rewarding as educating and empowering people. 
I found teaching more interesting than any other jobs. Does this motivate you to be a teacher?
```

## 使用RegEx Split拆分文本

```py
txt = '''I am teacher and  I love teaching.
There is nothing as rewarding as educating and empowering people.
I found teaching more interesting than any other jobs.
Does this motivate you to be a teacher?'''
print(re.split('\n', txt)) # 使用\n —— 行尾符号进行拆分
```

```sh
['I am teacher and  I love teaching.', 'There is nothing as rewarding as educating and empowering people.', 'I found teaching more interesting than any other jobs.', 'Does this motivate you to be a teacher?']
```

## 编写RegEx模式

要声明字符串变量，我们使用单引号或双引号。要声明正则表达式变量，使用*r''*。
以下模式仅识别小写的apple，要使其不区分大小写，要么重新编写模式，要么添加标志。

```py
import re

regex_pattern = r'apple'
txt = 'Apple and banana are fruits. An old cliche says an apple a day a doctor way has been replaced by a banana a day keeps the doctor far far away. '
matches = re.findall(regex_pattern, txt)
print(matches)  # ['apple']

# 要不区分大小写，请添加标志 '
matches = re.findall(regex_pattern, txt, re.I)
print(matches)  # ['Apple', 'apple']
# 或者我们可以使用一组字符方法
regex_pattern = r'[Aa]pple'  # 这意味着第一个字母可以是Apple或apple
matches = re.findall(regex_pattern, txt)
print(matches)  # ['Apple', 'apple']
```

* `[]`：一组字符
    - `[a-c]`表示a或b或c
    - `[a-z]`表示从a到z的任何字母
    - `[A-Z]`表示从A到Z的任何字符
    - `[0-3]`表示0或1或2或3
    - `[0-9]`表示从0到9的任何数字
    - `[A-Za-z0-9]`表示任何单个字符，即a到z、A到Z或0到9

- `\`：用于转义特殊字符
    - `\d`表示：匹配包含数字（0-9）的字符串
    - `\D`表示：匹配不包含数字的字符串
- `.`：任何字符，除了换行符(\n)
- `^`：以...开始
    - `r'^substring'` 例如`r'^love'`，以单词love开头的句子
    - `r'[^abc]`表示不是a、不是b、不是c。
- `$`：以...结束
    - `r'substring$'` 例如`r'love$'`，以单词love结尾的句子
- `*`：零次或多次
    - `r'[a]*'`表示a是可选的，或者它可以出现多次。
- `+`：一次或多次
    - `r'[a]+'`表示至少一次（或更多）
- `?`：零次或一次
    - `r'[a]?'`表示零次或一次
- `{3}`：恰好3个字符
- `{3,}`：至少3个字符
- `{3,8}`：3到8个字符
- `|`：要么是要么
    - `r'apple|banana'`表示要么是apple要么是banana
- `()`：捕获和分组

![正则表达式备忘单](./images/regex.png)

### 方括号`[]`

让我们使用方括号包含小写和大写字母

```py
regex_pattern = r'[Aa]pple' # this square bracket mean either A or a
txt = 'Apple and banana are fruits. An old cliche says an apple a day a doctor way has been replaced by a banana a day keeps the doctor far far away.'
matches = re.findall(regex_pattern, txt)
print(matches)  # ['Apple', 'apple']
```

如果我们想查找香蕉，我们将模式写成以下方式：

```py
regex_pattern = r'[Aa]pple|[Bb]anana' # 这个方括号表示要么是A要么是a
txt = 'Apple and banana are fruits. An old cliche says an apple a day a doctor way has been replaced by a banana a day keeps the doctor far far away.'
matches = re.findall(regex_pattern, txt)
print(matches)  # ['Apple', 'banana', 'apple', 'banana']
```

使用方括号和或运算符，我们成功提取了Apple、apple、Banana和banana。

### 正则表达式中的转义字符`\`

```py
regex_pattern = r'\d'  # d 是一个特殊字符，表示数字
txt = 'This regular expression example was made on December 6,  2019 and revised on July 8, 2021'
matches = re.findall(regex_pattern, txt)
print(matches)  # ['6', '2', '0', '1', '9', '8', '2', '0', '2', '1']，这不是我们想要的结果
```

### 一次或多次`+`

```py
regex_pattern = r'\d+'  # d 是一个特殊字符，表示数字，+ 表示一次或多次
txt = 'This regular expression example was made on December 6,  2019 and revised on July 8, 2021'
print(matches)  # ['6', '2019', '8', '2021'] - 现在，这更好！
```

### 句点Period`.`

```py
regex_pattern = r'[a].'  # 这个方括号表示a，. 表示除换行符以外的任何字符
txt = '''Apple and banana are fruits'''
matches = re.findall(regex_pattern, txt)
print(matches)  # ['an', 'an', 'an', 'a ', 'ar']

regex_pattern = r'[a].+'  # . 任何字符，+ 任何字符一次或多次
matches = re.findall(regex_pattern, txt)
print(matches)  # ['and banana are fruits']
```

### 零次或多次`*`

零次或多次。模式可以不出现，也可以出现多次。

```py
regex_pattern = r'[a].*'  # . 任何字符，* 任何字符零次或多次
txt = '''Apple and banana are fruits'''
matches = re.findall(regex_pattern, txt)
print(matches)  # ['and banana are fruits']
```

### 零次或一次`?`

零次或一次。模式可能不出现，也可能出现一次。

```py
txt = '''I am not sure if there is a convention how to write the word e-mail.
Some people write it as email others may write it as Email or E-mail.'''
regex_pattern = r'[Ee]-?mail'  # ? 这里表示'-'是可选的
matches = re.findall(regex_pattern, txt)
print(matches)  # ['e-mail', 'email', 'Email', 'E-mail']
```

### 正则表达式中的量词

我们可以使用花括号来指定我们在文本中正在寻找的子字符串的长度。假设我们对长度为4个字符的子字符串感兴趣：

```py
txt = 'This regular expression example was made on December 6,  2019 and revised on July 8, 2021'
regex_pattern = r'\d{4}'  # 确切四次
matches = re.findall(regex_pattern, txt)
print(matches)  # ['2019', '2021']

txt = 'This regular expression example was made on December 6,  2019 and revised on July 8, 2021'
regex_pattern = r'\d{1, 4}'   # 1 到 4 次
matches = re.findall(regex_pattern, txt)
print(matches)  # ['6', '2019', '8', '2021']
```

### 脱字符/插入符号caret `^`

- 以...开始

```py
txt = 'This regular expression example was made on December 6,  2019 and revised on July 8, 2021'
regex_pattern = r'^This'  # ^ 表示以...开始
matches = re.findall(regex_pattern, txt)
print(matches)  # ['This']
```

- 否定Negation

```py
txt = 'This regular expression example was made on December 6,  2019 and revised on July 8, 2021'
regex_pattern = r'[^A-Za-z ]+'  # ^ 集合字符中的 ^ 表示否定，不包括 A 到 Z，不包括 a 到 z，不包括空格
matches = re.findall(regex_pattern, txt)
print(matches)  # ['6,', '2019', '8', '2021']
```

## 💻 练习：第18天

### 练习：级别1

1. 在以下段落中，哪个单词最频繁出现？

```py
paragraph = 'I love teaching. If you do not love teaching what else can you love. I love Python if you do not love something which can give you all the capabilities to develop an application what else can you love.
```

```sh
    [
    (6, 'love'),
    (5, 'you'),
    (3, 'can'),
    (2, 'what'),
    (2, 'teaching'),
    (2, 'not'),
    (2, 'else'),
    (2, 'do'),
    (2, 'I'),
    (1, 'which'),
    (1, 'to'),
    (1, 'the'),
    (1, 'something'),
    (1, 'if'),
    (1, 'give'),
    (1, 'develop'),
    (1, 'capabilities'),
    (1, 'application'),
    (1, 'an'),
    (1, 'all'),
    (1, 'Python'),
    (1, 'If')
    ]
```

2. 在水平x轴上，一些粒子的位置是-12，-4，-3和-1在负方向，原点在0处，正方向为4和8。从整个文本中提取这些数字，并找到最远粒子之间的距离。

```py
points = ['-12', '-4', '-3', '-1', '0', '4', '8']
sorted_points =  [-12, -4, -3, -1, -1, 0, 2, 4, 8]
distance = 8 -(-12) # 20
```

### 练习：级别2

1. 编写一个模式，用于识别一个字符串是否是有效的Python变量

   ```sh
   is_valid_variable('first_name') # True
   is_valid_variable('first-name') # False
   is_valid_variable('1first_name') # False
   is_valid_variable('firstname') # True
   ```

###  练习：级别3

1. 清理以下文本。清理后，计算字符串中三个最常出现的单词。

   ```py
   sentence = '''%I $am@% a %tea@cher%, &and& I lo%#ve %tea@ching%;. There $is nothing; &as& mo@re rewarding as educa@ting &and& @emp%o@wering peo@ple. ;I found tea@ching m%o@re interesting tha@n any other %jo@bs. %Do@es thi%s mo@tivate yo@u to be a tea@cher!?'''
   
   print(clean_text(sentence));
   I am a teacher and I love teaching There is nothing as more rewarding as educating and empowering people I found teaching more interesting than any other jobs Does this motivate you to be a teacher
   print(most_frequent_words(cleaned_text)) # [(3, 'I'), (2, 'teaching'), (2, 'teacher')]
   ```

