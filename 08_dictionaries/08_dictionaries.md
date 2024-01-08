# 08 字典

## 字典

字典是一种无序、可修改（可变）的键值对（key: value）数据类型的集合。

### 创建字典

要创建一个字典，我们使用花括号 {} 或内置函数 *dict()*。

```py
# 语法
empty_dict = {}
# 带有数据值的字典
dct = {'key1':'value1', 'key2':'value2', 'key3':'value3', 'key4':'value4'}
```

**示例:**

```py
person = {
    'first_name':'Asabeneh',
    'last_name':'Yetayeh',
    'age':250,
    'country':'Finland',
    'is_married':True,
    'skills':['JavaScript', 'React', 'Node', 'MongoDB', 'Python'],
    'address':{
        'street':'Space street',
        'zipcode':'02210'
    }
    }
```

上面的字典示例显示值可以是任何数据类型：字符串、布尔值、列表、元组、集合或字典。

### 字典长度

它检查字典中的 'key: value' 对的数量。

```py
# 语法
dct = {'key1':'value1', 'key2':'value2', 'key3':'value3', 'key4':'value4'}
print(len(dct)) # 4
```

**示例:**

```py
person = {
    'first_name':'Asabeneh',
    'last_name':'Yetayeh',
    'age':250,
    'country':'Finland',
    'is_married':True,
    'skills':['JavaScript', 'React', 'Node', 'MongoDB', 'Python'],
    'address':{
        'street':'Space street',
        'zipcode':'02210'
    }
    }
print(len(person)) # 7
```

### 访问字典项

我们可以通过引用其键名来访问字典项。

```py
# 语法
dct = {'key1':'value1', 'key2':'value2', 'key3':'value3', 'key4':'value4'}
print(dct['key1']) # value1
print(dct['key4']) # value4
```

**示例:**

```py
person = {
    'first_name':'Asabeneh',
    'last_name':'Yetayeh',
    'age':250,
    'country':'Finland',
    'is_married':True,
    'skills':['JavaScript', 'React', 'Node', 'MongoDB', 'Python'],
    'address':{
        'street':'Space street',
        'zipcode':'02210'
    }
    }
print(person['first_name']) # Asabeneh
print(person['country'])    # Finland
print(person['skills'])     # ['JavaScript', 'React', 'Node', 'MongoDB', 'Python']
print(person['skills'][0])  # JavaScript
print(person['address']['street']) # Space street
print(person['city'])       # 错误
```

通过键名访问项会在键不存在时引发错误。为了避免这种错误，首先我们必须检查键是否存在，或者我们可以使用 _get_ 方法。get 方法如果键不存在，则返回一个 None，这是一个 NoneType 对象数据类型。

```py
person = {
    'first_name':'Asabeneh',
    'last_name':'Yetayeh',
    'age':250,
    'country':'Finland',
    'is_married':True,
    'skills':['JavaScript', 'React', 'Node', 'MongoDB', 'Python'],
    'address':{
        'street':'Space street',
        'zipcode':'02210'
    }
    }
print(person.get('first_name')) # Asabeneh
print(person.get('country'))    # Finland
print(person.get('skills')) #['HTML','CSS','JavaScript', 'React', 'Node', 'MongoDB', 'Python']
print(person.get('city'))   # None
```

### 向字典中添加项

我们可以向字典中添加新的键值对

```py
# 语法
dct = {'key1':'value1', 'key2':'value2', 'key3':'value3', 'key4':'value4'}
dct['key5'] = 'value5'
```

**示例:**

```py
person = {
    'first_name':'Asabeneh',
    'last_name':'Yetayeh',
    'age':250,
    'country':'Finland',
    'is_married':True,
    'skills':['JavaScript', 'React', 'Node', 'MongoDB', 'Python'],
    'address':{
        'street':'Space street',
        'zipcode':'02210'
        }
}
person['job_title'] = 'Instructor'
person['skills'].append('HTML')
print(person)
```

### 修改字典中的项

我们可以修改字典中的项

```py
# 语法
dct = {'key1':'value1', 'key2':'value2', 'key3':'value3', 'key4':'value4'}
dct['key1'] = 'value-one'
```

**示例:**

```py
person = {
    'first_name':'Asabeneh',
    'last_name':'Yetayeh',
    'age':250,
    'country':'Finland',
    'is_married':True,
    'skills':['JavaScript', 'React', 'Node', 'MongoDB', 'Python'],
    'address':{
        'street':'Space street',
        'zipcode':'02210'
    }
    }
person['first_name'] = 'Eyob'
person['age'] = 252
```

### 检查字典中的键

我们使用 _in_ 运算符来检查字典中是否存在键

```py
# 语法
dct = {'key1':'value1', 'key2':'value2', 'key3':'value3', 'key4':'value4'}
print('key2' in dct) # True
print('key5' in dct) # False
```

### 从字典中删除键值对

- _pop(key)_: 移除具有指定键名的项
- _popitem()_: 移除最后一个项
- _del_: 移除具有指定键名的项

```py
# 语法
dct = {'key1':'value1', 'key2':'value2', 'key3':'value3', 'key4':'value4'}
dct.pop('key1') # 移除 key1 项
dct = {'key1':'value1', 'key2':'value2', 'key3':'value3', 'key4':'value4'}
dct.popitem() # 移除最后一项


del dct['key2'] # 移除 key2 项
```

**示例:**

```py
person = {
    'first_name':'Asabeneh',
    'last_name':'Yetayeh',
    'age':250,
    'country':'Finland',
    'is_married':True,
    'skills':['JavaScript', 'React', 'Node', 'MongoDB', 'Python'],
    'address':{
        'street':'Space street',
        'zipcode':'02210'
    }
    }
person.pop('first_name')        # 移除 firstname 项
person.popitem()                # 移除 address 项
del person['is_married']        # 移除 is_married 项
```

### 将字典转换为项的列表

_items()_ 方法将字典转换为项的元组列表。

```py
# 语法
dct = {'key1':'value1', 'key2':'value2', 'key3':'value3', 'key4':'value4'}
print(dct.items()) # dict_items([('key1', 'value1'), ('key2', 'value2'), ('key3', 'value3'), ('key4', 'value4')])
```

### 清空字典

如果我们不想要字典中的项，可以使用 _clear()_ 方法将其清空

```py
# 语法
dct = {'key1':'value1', 'key2':'value2', 'key3':'value3', 'key4':'value4'}
print(dct.clear()) # None
```

### 删除字典

如果我们不使用字典，可以完全删除它

```py
# 语法
dct = {'key1':'value1', 'key2':'value2', 'key3':'value3', 'key4':'value4'}
del dct
```

### 复制字典

我们可以使用 _copy()_ 方法复制一个字典。使用复制，我们可以避免修改原始字典。

```py
# 语法
dct = {'key1':'value1', 'key2':'value2', 'key3':'value3', 'key4':'value4'}
dct_copy = dct.copy() # {'key1':'value1', 'key2':'value2', 'key3':'value3', 'key4':'value4'}
```

### 将字典的键作为列表获取

_keys()_ 方法将字典的所有键作为列表返回。

```py
# 语法
dct = {'key1':'value1', 'key2':'value2', 'key3':'value3', 'key4':'value4'}
keys = dct.keys()
print(keys)     # dict_keys(['key1', 'key2', 'key3', 'key4'])
```

### 将字典的值作为列表获取

_values_ 方法将字典的所有值作为列表返回。

```py
# 语法
dct = {'key1':'value1', 'key2':'value2', 'key3':'value3', 'key4':'value4'}
values = dct.values()
print(values)     # dict_values(['value1', 'value2', 'value3', 'value4'])
```

## 💻 练习: 第8天

1. 创建一个名为 "dog" 的空字典。
2. 向 "dog" 字典添加名字、颜色、品种、腿数和年龄等键值对。
3. 创建一个名为 "student" 的字典，并添加 "first_name"、"last_name"、"gender"、"age"、"marital_status"、"skills"、"country"、"city" 和 "address" 作为键。
4. 获取 "student" 字典的长度。
5. 获取 "skills" 的值并检查其数据类型，应该是一个列表。
6. 修改 "skills" 的值，添加一个或两个技能。
7. 获取字典的键作为一个列表。
8. 获取字典的值作为一个列表。
9. 使用 _items()_ 方法将字典变为一个元组列表。
10. 删除字典中的一项。
11. 删除一个字典。
