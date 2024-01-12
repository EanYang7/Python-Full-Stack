# 19 文件处理

## 文件处理

到目前为止，我们已经看到了不同的Python数据类型。通常，我们会将我们的数据存储在不同的文件格式中。除了处理文件，本节还将介绍不同的文件格式（.txt，.json，.xml，.csv，.tsv，.excel）。首先，让我们熟悉使用常见文件格式（.txt）处理文件。

文件处理是编程的重要部分，它允许我们创建、读取、更新和删除文件。在Python中，我们使用内置函数`open()`来处理数据。

```py
# 语法
open('filename', mode) # 模式（r，a，w，x，t，b）可以是读取、写入、更新
```

- "r" - 读取 - 默认值。打开文件进行读取，如果文件不存在则返回错误
- "a" - 追加 - 打开文件以进行追加，如果文件不存在则创建文件
- "w" - 写入 - 打开文件以进行写入，如果文件不存在则创建文件
- "x" - 创建 - 创建指定的文件，如果文件存在则返回错误
- "t" - 文本 - 默认值。文本模式
- "b" - 二进制 - 二进制模式（例如图像）

### 打开文件进行读取

_open_ 的默认模式是读取，所以我们不需要指定'r'或'rt'。我已经创建并保存了一个名为reading_file_example.txt的文件在files目录中。让我们看看是如何做的：

```py
f = open('./files/reading_file_example.txt')
print(f) # <_io.TextIOWrapper name='./files/reading_file_example.txt' mode='r' encoding='UTF-8'>
```

如您所见，在上面的示例中，我打印了打开的文件，并且它提供了一些关于它的信息。打开的文件具有不同的读取方法：_read()_，_readline_，_readlines_。打开的文件必须使用`close()`方法关闭。

- _read()_：将整个文本读取为字符串。如果我们想要限制要读取的字符数，可以通过将int值传递给*read(number)*方法来限制它。

```py
f = open('./files/reading_file_example.txt')
txt = f.read()
print(type(txt))
print(txt)
f.close()
```

```sh
# 输出
<class 'str'>
This is an example to show how to open a file and read.
This is the second line of the text.
```

让我们不打印所有的文本，而是打印文本文件的前10个字符。

```py
f = open('./files/reading_file_example.txt')
txt = f.read(10)
print(type(txt))
print(txt)
f.close()
```

```sh
# 输出
<class 'str'>
This is an
```

- _readline()_：只读取第一行

```py
f = open('./files/reading_file_example.txt')
line = f.readline()
print(type(line))
print(line)
f.close()
```

```sh
# 输出
<class 'str'>
This is an example to show how to open a file and read.
```

- _readlines()_：逐行读取所有文本并返回行的列表

```py
f = open('./files/reading_file_example.txt')
lines = f.readlines()
print(type(lines))
print(lines)
f.close()
```

```sh
# 输出
<class 'list'>
['This is an example to show how to open a file and read.\n', 'This is the second line of the text.']
```

以另一种方式获取所有行作为列表的方法是使用`splitlines()`：

```py
f = open('./files/reading_file_example.txt')
lines = f.read().splitlines()
print(type(lines))
print(lines)
f.close()
```

```sh
# 输出
<class 'list'>
['This is an example to show how to open a file and read.', 'This is the second line of the text.']
```

打开文件后，我们应该关闭它。很容易忘记关闭它们。有一种新的打开文件的方法，使用`with` - 它会自动关闭文件。让我们用`with`方法重新编写上一个示例：

```py
with open('./files/reading_file_example.txt') as f:
    lines = f.read().splitlines()
    print(type(lines))
    print(lines)
```

```sh
# 输出
<class 'list'>
['This is an example to show how to open a file and read.', 'This is the second line of the text.']
```

### 打开文件进行写入和更新

要向现有文件写入内容，我们必须将模式添加为`open()`函数的参数：

- "a" - 追加 - 将附加到文件的末尾，如果文件不存在则创建新文件。
- "w" - 写入 - 将覆盖任何现有内容，如果文件不存在则创建。

让我们在阅读的文件中添加一些文本：

```py
with open('./files/reading_file_example.txt','a') as f:
    f.write('这个文本将追加到末尾')
```

下面的方法将创建一个新文件，如果文件不存在：

```py
with open('./files/writing_file_example.txt','w') as f:
    f.write('这个文本将写入新创建的文件')
```

### 删除文件

在前一节中，我们已经看到了如何使用`os`模块创建和删除目录。现在，如果我们想要删除一个文件，我们使用`os`模块。

```py
import os
os.remove('./files/example.txt')

```

如果文件不存在，删除方法将引发错误，因此最好使用这样的条件：

```py
import os
if os.path.exists('./files/example.txt'):
    os.remove('./files/example.txt')
else:
    print('文件不存在')
```

## 文件类型

### 带有txt扩展名的文件

带有`txt`扩展名的文件是一种非常常见的数据形式。

### 带有json扩展名的文件

JSON代表JavaScript对象表示法(JavaScript Object Notation)。实际上，它是一个字符串化的JavaScript对象或Python字典。

_示例：_

```py
# 字典
person_dct= {
    "name":"Asabeneh",
    "country":"Finland",
    "city":"Helsinki",
    "skills":["JavaScrip", "React","Python"]
}
# JSON：来自字典的字符串形式
person_json = "{'name': 'Asabeneh', 'country': 'Finland', 'city': 'Helsinki', 'skills': ['JavaScrip', 'React', 'Python']}"

# 我们使用三个引号并将其分为多行以使其更易读
person_json = '''{
    "name":"Asabeneh",
    "country":"Finland",
    "city":"Helsinki",
    "skills":["JavaScrip", "React","Python"]
}'''
```

### 将JSON更改为字典

要将JSON更改为字典，首先我们导入json模块，然后使用`loads`方法。

```py
import json
# JSON
person_json = '''{
    "name": "Asabeneh",
    "country": "Finland",
    "city": "Helsinki",
    "skills": ["JavaScrip", "React", "Python"]
}'''
# 让我们将JSON更改为字典
person_dct = json.loads(person_json)
print(type(person_dct))
print(person_dct)
print(person_dct['name'])
```

```sh
# 输出
<class 'dict'>
{'name': 'Asabeneh', 'country': 'Finland', 'city': 'Helsinki', 'skills': ['JavaScrip', 'React', 'Python']}
Asabeneh
```

### 将字典更改为JSON

要将字典更改为JSON，我们使用json模块的`dumps`方法。

```py
import json
# python字典
person = {
    "name": "Asabeneh",
    "country": "Finland",
    "city": "Helsinki",
    "skills": ["JavaScrip", "React", "Python"]
}
# 让我们将其转换为json
person_json = json.dumps(person, indent=4) # 缩进可以是2、4、8。它美化了json
print(type(person_json))
print(person_json)
```

```sh
# 输出
# 当您打印它时，它不会带引号，但实际上它是一个字符串
# JSON没有类型，它是一个字符串类型。
<class 'str'>
{
    "name": "Asabeneh",
    "country": "Finland",
    "city": "Helsinki",
    "skills": [
        "JavaScrip",
        "React",
        "Python"
    ]
}
```

### 保存为JSON文件

我们还可以将我们的数据保存为JSON文件。让我们使用以下步骤将其保存为JSON文件。对于编写JSON文件，我们使用json.dump()方法，它可以接受字典、输出文件、ensure_ascii和缩进。

```py
import json
# python字典
person = {
    "name": "Asabeneh",
    "country": "Finland",
    "city": "Helsinki",
    "skills": ["JavaScrip", "React", "Python"]
}
with open('./files/json_example.json', 'w', encoding='utf-8') as f:
    json.dump(person, f, ensure_ascii=False, indent=4)
```

上面的代码中使用了编码和缩进。缩进使json文件易于阅读。

### 带有csv扩展名的文件

CSV代表逗号分隔值。CSV是一种用于存储表格数据的简单文件格式，例如电子表格或数据库。CSV是数据科学中非常常见的数据格式。

**示例：**

```csv
"name","country","city","skills"
"Asabeneh","Finland","Helsinki","JavaScript"
```

**示例：**

```py
import csv
with open('./files/csv_example.csv') as f:
    csv_reader = csv.reader(f, delimiter=',') # 我们使用reader方法来读取csv
    line_count = 0
    for row in csv_reader:
        if line_count == 0:
            print(f'列名为 :{", ".join(row)}')
            line_count += 1
        else:
            print(
                f'\t{row[0]} 是一位老师。他住在{row[1]}, {row[2]}。')
            line_count += 1
    print(f'行数:  {line_count}')
```

```sh
# 输出:
列名为 :name, country, city, skills
        Asabeneh 是一位老师。他住在Finland, Helsinki。
行数:  2
```

### 带有xlsx扩展名的文件

要读取excel文件，我们需要安装`xlrd`包。

```py
import xlrd
excel_book = xlrd.open_workbook('sample.xls)
print(excel_book.nsheets)
print(excel_book.sheet_names)
```

### 带有xml扩展名的文件

XML是另一种结构化数据格式，它看起来像HTML。在XML中，标签不是预定义的。第一行是XML声明。person标签是XML的根。person具有一个gender属性。
**示例：XML**

```xml
<?xml version="1.0"?>
<person gender="female">
  <name>Asabeneh</name>
  <country>Finland</country>
  <city>Helsinki</city>
  <skills>
    <skill>JavaScrip</skill>
    <skill>React</skill>
    <skill>Python</skill>
  </skills>
</person>
```

有关如何读取XML文件的更多信息，请查看[文档](https://docs.python.org/3.12/library/xml.etree.elementtree.html)。

```py
import xml.etree.ElementTree as ET
tree = ET.parse('./files/xml_example.xml')
root = tree.getroot()
print('根标签:', root.tag)
print('属性:', root.attrib)
for child in root:
    print('字段: ', child.tag)
```

```sh
# 输出
根标签: person
属性: {'gender': 'male'}
字段: name
字段: country
字段: city
字段: skills
```

## 💻 练习：第19天

### 练习：级别1

1. 编写一个函数，用于统计文本中的行数和单词数。所有文件都在data文件夹中：
   a) 读取obama_speech.txt文件并统计行数和单词数
   b) 读取michelle_obama_speech.txt文件并统计行数和单词数
   c) 读取donald_speech.txt文件并统计行数和单词数
   d) 读取melina_trump_speech.txt文件并统计行数和单词数

2. 读取data目录中的countries_data.json数据文件，创建一个函数来找到十种最常使用的语言

   ```py
   # 输出应如下所示
   print(most_spoken_languages(filename='./data/countries_data.json', 10))
   [(91, 'English'),
   (45, 'French'),
   (25, 'Arabic'),
   (24, 'Spanish'),
   (9, 'Russian'),
   (9, 'Portuguese'),
   (8, 'Dutch'),
   (7, 'German'),
   (5, 'Chinese'),
   (4, 'Swahili'),
   (4, 'Serbian')]
   
   # 输出应如下所示
   print(most_spoken_languages(filename='./data/countries_data.json', 3))
   [(91, 'English'),
   (45, 'French'),
   (25, 'Arabic')]
   ```

3. 读取data目录中的countries_data.json数据文件，创建一个函数来创建一个包含十个最多人口的国家的列表

   ```py
   # 输出应如下所示
   print(most_populated_countries(filename='./data/countries_data.json', 10))
   
   [
   {'country': 'China', 'population': 1377422166},
   {'country': 'India', 'population': 1295210000},
   {'country': 'United States of America', 'population': 323947000},
   {'country': 'Indonesia', 'population': 258705000},
   {'country': 'Brazil', 'population': 206135893},
   {'country': 'Pakistan', 'population': 194125062},
   {'country': 'Nigeria', 'population': 186988000},
   {'country': 'Bangladesh', 'population': 161006790},
   {'country': 'Russian Federation', 'population': 146599183},
   {'country': 'Japan', 'population': 126960000}
   ]
   
   # 输出应如下所示
   
   print(most_populated_countries(filename='./data/countries_data.json', 3))
   [
   {'country': 'China', 'population': 1377422166},
   {'country': 'India', 'population': 1295210000},
   {'country': 'United States of America', 'population': 323947000}
   ]
   ```

### 练习：级别2

4. 从email_exchange_big.txt文件中提取所有收件箱电子邮件地址并将其存储为列表。
5. 找出英语中最常见的单词。将你的函数命名为find_most_common_words，它将接受两个参数 - 一个字符串或文件以及一个正整数，表示单词的数量。你的函数将以降序返回一个元组数组。检查输出。

```py
    # 输出应如下所示
    print(find_most_common_words('sample.txt', 10))
    [(10, 'the'),
    (8, 'be'),
    (6, 'to'),
    (6, 'of'),
    (5, 'and'),
    (4, 'a'),
    (4, 'in'),
    (3, 'that'),
    (2, 'have'),
    (2, 'I')]

    # 输出应如下所示
    print(find_most_common_words('sample.txt', 5))

    [(10, 'the'),
    (8, 'be'),
    (6, 'to'),
    (6, 'of'),
    (5, 'and')]
```

6. 使用函数find_most_frequent_words来查找：
   a) [奥巴马演讲](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/data/obama_speech.txt)中使用最频繁的十个词
   b) [米歇尔演讲](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/data/michelle_obama_speech.txt)中使用最频繁的十个词
   c) [特朗普演讲](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/data/donald_speech.txt)中使用最频繁的十个词
   d) [梅琳娜演讲](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/data/melina_trump_speech.txt)中使用最频繁的十个词
7. 编写一个Python应用程序，用于检查两个文本之间的相似性。它接受一个文件或字符串作为参数，并评估两个文本之间的相似性。例如，检查[米歇尔](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/data/michelle_obama_speech.txt)和[梅琳娜](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/data/melina_trump_speech.txt)演讲的文本之间的相似性。你可能需要几个函数，一个用于清理文本（clean_text），一个用于删除停用词（remove_support_words），最后一个用于检查相似性（check_text_similarity）。[停用词列表](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/data/stop_words.py)位于data目录中。
8. 找出romeo_and_juliet.txt中重复次数最多的10个单词。
9. 读取[hacker news csv](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/data/hacker_news.csv)文件并找出：
   a) 包含python或Python的行数
   b) 包含JavaScript、javascript或Javascript的行数
   c) 包含Java但不包含JavaScript的行数
