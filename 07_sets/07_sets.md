# 07 集合

## 集合

集合是一组项的集合。

数学中对集合的定义也可以应用到Python中。集合是一组无序、无索引的不同元素。在Python中，集合用于存储唯一的项，可以在集合之间找到 _并集_、_交集_、_差集_、_对称差_、_子集_、_超集_ 和 _不相交集_ 等操作。

### 创建集合

我们使用内置的 _set()_ 函数来创建集合。

- 创建一个空集合

```py
# 语法
st = set()
```

- 创建带有初始项的集合

```py
# 语法
st = {'item1', 'item2', 'item3', 'item4'}
```

**示例:**

```py
# 语法
fruits = {'banana', 'orange', 'mango', 'lemon'}
```

### 获取集合的长度

我们使用 **len()** 方法来查找集合的长度。

```py
# 语法
st = {'item1', 'item2', 'item3', 'item4'}
len(st)
```

**示例:**

```py
fruits = {'banana', 'orange', 'mango', 'lemon'}
len(fruits)
```

### 访问集合中的项

我们使用循环来访问项。我们将在循环部分中看到这一点。

### 检查项

要检查列表中是否存在项，我们使用 _in_ 成员运算符。

```py
# 语法
st = {'item1', 'item2', 'item3', 'item4'}
print("集合 st 是否包含 item3? ", 'item3' in st) # 集合 st 是否包含 item3? True
```

**示例:**

```py
fruits = {'banana', 'orange', 'mango', 'lemon'}
print('mango' in fruits) # True
```

### 向集合中添加项

一旦创建了集合，我们就不能更改任何项，但可以添加其他项。

- 使用 _add()_ 添加一个项

```py
# 语法
st = {'item1', 'item2', 'item3', 'item4'}
st.add('item5')
```

**示例:**

```py
fruits = {'banana', 'orange', 'mango', 'lemon'}
fruits.add('lime')
```

- 使用 _update()_ 添加多个项
  _update()_ 允许向集合中添加多个项。_update()_ 方法接受一个列表参数。

```py
# 语法
st = {'item1', 'item2', 'item3', 'item4'}
st.update(['item5','item6','item7'])
```

**示例:**

```py
fruits = {'banana', 'orange', 'mango', 'lemon'}
vegetables = ('tomato', 'potato', 'cabbage','onion', 'carrot')
fruits.update(vegetables)
```

### 从集合中删除项

我们可以使用 _remove()_ 方法从集合中删除项。如果找不到项，_remove()_ 方法将引发错误，因此最好检查项是否存在于给定的集合中。然而，_discard()_ 方法不会引发任何错误。

```py
# 语法
st = {'item1', 'item2', 'item3', 'item4'}
st.remove('item2')
```

pop() 方法从列表中删除一个随机项，并返回已删除的项。

**示例:**

```py
fruits = {'banana', 'orange', 'mango', 'lemon'}
fruits.pop()  # 从集合中删除一个随机项
```

如果我们对已删除的项感兴趣。

```py
fruits = {'banana', 'orange', 'mango', 'lemon'}
removed_item = fruits.pop() 
```

### 清空集合中的项

如果要清空集合，我们使用 _clear_ 方法。

```py
# 语法
st = {'item1', 'item2', 'item3', 'item4'}
st.clear()
```

**示例:**

```py
fruits = {'banana', 'orange', 'mango', 'le

mon'}
fruits.clear()
print(fruits) # set()
```

### 删除集合

如果要删除集合本身，我们使用 _del_ 运算符。

```py
# 语法
st = {'item1', 'item2', 'item3', 'item4'}
del st
```

**示例:**

```py
fruits = {'banana', 'orange', 'mango', 'lemon'}
del fruits
```

### 将列表转换为集合

我们可以将列表转换为集合，集合转换为列表。将列表转换为集合会删除重复项，只保留唯一项。

```py
# 语法
lst = ['item1', 'item2', 'item3', 'item4', 'item1']
st = set(lst)  # {'item2', 'item4', 'item1', 'item3'} - 顺序是随机的，因为集合通常是无序的
```

**示例:**

```py
fruits = ['banana', 'orange', 'mango', 'lemon','orange', 'banana']
fruits = set(fruits) # {'mango', 'lemon', 'banana', 'orange'}
```

### 合并集合

我们可以使用 _union()_ 或 _update()_ 方法合并两个集合。

- union
  该方法返回一个新的集合

```py
# 语法
st1 = {'item1', 'item2', 'item3', 'item4'}
st2 = {'item5', 'item6', 'item7', 'item8'}
st3 = st1.union(st2)
```

**示例:**

```py
fruits = {'banana', 'orange', 'mango', 'lemon'}
vegetables = {'tomato', 'potato', 'cabbage','onion', 'carrot'}
print(fruits.union(vegetables)) # {'lemon', 'carrot', 'tomato', 'banana', 'mango', 'orange', 'cabbage', 'potato', 'onion'}
```

- update
  该方法将一个集合插入到另一个集合中

```py
# 语法
st1 = {'item1', 'item2', 'item3', 'item4'}
st2 = {'item5', 'item6', 'item7', 'item8'}
st1.update(st2) # 将 st2 的内容添加到 st1 中
```

**示例:**

```py
fruits = {'banana', 'orange', 'mango', 'lemon'}
vegetables = {'tomato', 'potato', 'cabbage','onion', 'carrot'}
fruits.update(vegetables)
print(fruits) # {'lemon', 'carrot', 'tomato', 'banana', 'mango', 'orange', 'cabbage', 'potato', 'onion'}
```

### 查找两个集合的交集项

交集返回两个集合中都存在的项。请参见示例

```py
# 语法
st1 = {'item1', 'item2', 'item3', 'item4'}
st2 = {'item3', 'item2'}
st1.intersection(st2) # {'item3', 'item2'}
```

**示例:**

```py
whole_numbers = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10}
even_numbers = {0, 2, 4, 6, 8, 10}
whole_numbers.intersection(even_numbers) # {0, 2, 4, 6, 8, 10}

python = {'p', 'y', 't', 'h', 'o','n'}
dragon = {'d', 'r', 'a', 'g', 'o','n'}
python.intersection(dragon)     # {'o', 'n'}
```

### 检查子集和超集

一个集合可以是其他集合的子集或超集：

- 子集: _issubset()_
- 超集: _issuperset()_

```py
# 语法
st1 = {'item1', 'item2', 'item3', 'item4'}
st2 = {'item2', 'item3'}
st2.issubset(st1) # True
st1.issuperset(st2) # True
```

**示例:**

```py
whole_numbers = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10}
even_numbers = {0, 2, 4, 6, 8, 10}
whole_numbers.issubset(even_numbers) # False，因为它是超集
whole_numbers.issuperset(even_numbers) # True

python = {'p', 'y', 't', 'h', 'o','n'}
dragon = {'d', 'r', 'a', 'g', 'o','n'}
python.issubset(dragon)     # False
```

### 检查两个集合之间的差异

它返回两个集合之间的差异。

```py
# 语法
st1 = {'item1', 'item2', 'item3', 'item4'}
st2 = {'item2', 'item3'}
st2.difference(st1) # set()
st1.difference(st2) # {'item1', 'item4'} => st1\st2
```

**示例:**

```py
whole_numbers = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10}
even_numbers = {0, 2, 4, 6, 8, 10}
whole_numbers.difference(even_numbers) # {1, 3, 5, 7, 9}

python = {'p', 'y', 't', 'o','n'}
dragon = {'d', 'r', 'a', 'g', 'o','n'}
python.difference(dragon)     # {'p', 'y', 't'}  - 结果是无序的（集合的特点）
dragon.difference(python)     # {'d', 'r', 'a', 'g'}
```

### 寻找两个集合的对称差异

它返回两个集合之间的对称差异symmetric difference。这意味着它返回一个包含两个集合中的所有项，但不包含同时存在于两个集合中的项的集合，数学上表示为：(A\B) ∪ (B\A)

```python
# 语法
st1 = {'item1', 'item2', 'item3', 'item4'}
st2 = {'item2', 'item3'}
# 这意味着 (A\B)∪(B\A)
st2.symmetric_difference(st1) # {'item1', 'item4'}
```

**示例:**

```python
whole_numbers = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10}
some_numbers = {1, 2, 3, 4, 5}
whole_numbers.symmetric_difference(some_numbers) # {0, 6, 7, 8, 9, 10}

python = {'p', 'y', 't', 'h', 'o','n'}
dragon = {'d', 'r', 'a', 'g', 'o','n'}
python.symmetric_difference(dragon)  # {'r', 't', 'p', 'y', 'g', 'a', 'd', 'h'}
```

### 连接集合

如果两个集合没有共同的项，我们称它们为不相交集合。我们可以使用 _isdisjoint()_ 方法来检查两个集合是否是相交的或不相交的。

```python
# 语法
st1 = {'item1', 'item2', 'item3', 'item4'}
st2 = {'item2', 'item3'}
st2.isdisjoint(st1) # False
```

**示例:**

```python
even_numbers = {0, 2, 4 ,6, 8}
even_numbers = {1, 3, 5, 7, 9}
even_numbers.isdisjoint(odd_numbers) # True，因为没有共同项

python = {'p', 'y', 't', 'h', 'o','n'}
dragon = {'d', 'r', 'a', 'g', 'o','n'}
python.isdisjoint(dragon)  # False，有共同项 {'o', 'n'}
```
## 💻 练习：第 7 天

```python
# 集合
it_companies = {'Facebook', 'Google', 'Microsoft', 'Apple', 'IBM', 'Oracle', 'Amazon'}
A = {19, 22, 24, 20, 25, 26}
B = {19, 22, 20, 25, 26, 24, 28, 27}
age = [22, 19, 24, 25, 26, 24, 25, 24]
```

### 练习：级别 1

1. 查找集合 it_companies 的长度。
2. 将 'Twitter' 添加到 it_companies 中。
3. 一次性将多个 IT 公司插入到集合 it_companies 中。
4. 从集合 it_companies 中删除一个公司。
5. remove 和 discard 之间的区别是什么？

### 练习：级别 2

1. 连接 A 和 B。
2. 查找 A 和 B 的交集。
3. A 是否为 B 的子集？
4. A 和 B 是否为不相交集？
5. 将 A 与 B 连接，然后将 B 与 A 连接。
6. A 和 B 之间的对称差异是什么？
7. 完全删除这些集合。

### 练习：级别 3

1. 将年龄转换为集合，并比较列表和集合的长度，哪一个更大？
2. 解释以下数据类型之间的区别：字符串、列表、元组和集合。
3. _我是一名教师，我热爱启发和教育人们。_ 这个句子中使用了多少个独特的单词？使用分割方法和集合来获取独特的单词。
