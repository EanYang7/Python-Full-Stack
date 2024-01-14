# 06 元组

## 元组

元组是一个包含不同数据类型的有序且不可变（不可修改）的集合。元组用圆括号 `()` 表示。一旦创建了元组，我们就不能更改它的值。因为元组是不可修改的，所以我们不能使用 `add`、`insert`、`remove` 等方法。与列表不同，元组有很少的方法。与元组相关的方法有：

- `tuple()`: 创建一个空元组
- `count()`: 计算元组中指定项目的数量
- `index()`: 查找元组中指定项目的索引
- `+` 运算符: 连接两个或多个元组，创建一个新的元组

### 创建元组

- 空元组：创建一个空元组

  ```python
  # 语法
  empty_tuple = ()
  # 或使用元组构造函数
  empty_tuple = tuple()
  ```

- 带有初始值的元组

  ```python
  # 语法
  tpl = ('item1', 'item2','item3')
  ```

  ```python
  fruits = ('banana', 'orange', 'mango', 'lemon')
  ```

### 元组长度

我们使用 `len()` 方法来获取元组的长度。

```python
# 语法
tpl = ('item1', 'item2', 'item3')
len(tpl)
```

### 访问元组项目

- 正向索引
  与列表数据类型类似，我们使用正向或负向索引来访问元组项目。
  

![访问元组项目](./images/tuples_index.png)

```python
# 语法
tpl = ('item1', 'item2', 'item3')
first_item = tpl[0]
second_item = tpl[1]
```

```python
fruits = ('banana', 'orange', 'mango', 'lemon')
first_fruit = fruits[0]
second_fruit = fruits[1]
last_index = len(fruits) - 1
last_fruit = fruits[last_index]
```

- 负向索引
  负向索引表示从末尾开始，-1 表示最后一个项目，-2 表示倒数第二个项目，以此类推。


![元组负向索引](./images/tuple_negative_indexing.png)

```python
# 语法
tpl = ('item1', 'item2', 'item3','item4')
first_item = tpl[-4]
second_item = tpl[-3]
```

```python
fruits = ('banana', 'orange', 'mango', 'lemon')
first_fruit = fruits[-4]
second_fruit = fruits[-3]
last_fruit = fruits[-1]
```

### 切片元组

我们可以通过指定元组中的索引范围来切片出一个子元组，返回值将是一个包含指定项目的新元组。

- 正向索引范围

  ```python
  # 语法
  tpl = ('item1', 'item2', 'item3','item4')
  all_items = tpl[0:4]         # 所有项目
  all_items = tpl[0:]          # 所有项目
  middle_two_items = tpl[1:3]  # 不包括索引 3 处的项目
  ```

  ```python
  fruits = ('banana', 'orange', 'mango', 'lemon')
  all_fruits = fruits[0:4]    # 所有项目
  all_fruits = fruits[0:]     # 所有项目
  orange_mango = fruits[1:3]  # 不包括索引 3 处的项目
  orange_to_the_rest = fruits[1:]
  ```

- 负向索引范围

  ```python
  # 语法
  tpl = ('item1', 'item2', 'item3','item4')
  all_items = tpl[-4:]          # 所有项目
  middle_two_items = tpl[-3:-1]  # 不包括索引 3 (-1) 处的项目
  ```

  ```python
  fruits = ('banana', 'orange', 'mango', 'lemon')
  all_fruits = fruits[-4:]      # 所有项目
  orange_mango = fruits[-3:-1]  # 不包括索引 3 处的项目
  orange_to_the_rest = fruits[-3:]
  ```

### 将元组更改为列表

我们可以将元组更改为列表，也可以将列表更改为元组。元组是不可变的，如果我们想要修改一个元组，我们应该将其更改为列表。

```python
# 语法
tpl = ('item1', 'item2', 'item3','item4')
lst = list(tpl)
```

```python
fruits = ('banana', 'orange', 'mango', 'lemon')
fruits = list(fruits)
fruits[0] = 'apple'
print(fruits)     # ['apple', 'orange', 'mango', 'lemon']
fruits = tuple(fruits)
print(fruits)     # ('apple', 'orange', 'mango', 'lemon')
```

### 检查元组中的项目

我们可以使用 `in` 来检查元组中是否存在某个项目，它会返回一个布尔值。

```python
# 语法
tpl = ('item1', 'item2', 'item3','item4')
'item2' in tpl # True
```

```python
fruits = ('banana', 'orange', 'mango', 'lemon')
print('orange' in fruits) # True
print('apple' in fruits) # False
fruits[0] = 'apple' # TypeError:“tuple”对象不支持项分配
```

### 连接元组

我们可以使用 `+` 运算符来连接两个或多个元组。

```python
# 语法
tpl1 = ('item1', 'item2', 'item3')
tpl2 = ('item4', 'item5','item6')
tpl3 = tpl1 + tpl2
```

```python
fruits = ('banana', 'orange', 'mango', 'lemon')
vegetables = ('Tomato', 'Potato', 'Cabbage','Onion', 'Carrot')
fruits_and_vegetables = fruits + vegetables
```

### 删除元组

不能删除元组中的单个项目，但可以使用 `del` 删除整个元组。

```python
# 语法
tpl1 = ('item1', 'item2', 'item3')
del tpl1
```

```python
fruits = ('banana', 'orange', 'mango', 'lemon')
del fruits
```

🌕 你太勇敢了，已经走到了这一步。你刚刚完成了第 6 天的挑战，距离伟大的目标又前进了 6 步。现在为你的大脑和肌肉做一些锻炼。

## 💻 练习：第 6 天

### 练习：级别 1

1. 创建一个空元组。
2. 创建一个包含你的姐妹和兄弟的姓名的元组（想象中的兄弟姐妹也可以）。
3. 连接兄弟和姐妹的元组，并将其赋值给 `siblings`。
4. 你有多少个兄弟姐妹？
5. 修改 `siblings` 元组，添加你父亲和母亲的姓名，并将其赋值给 `family_members`。

### 练习：级别 2

1. 从 `family_members` 中解包出兄弟姐妹和父母。
2. 创建水果、蔬菜和动物产品的元组。连接这三个元组，并将其赋值给一个名为 `food_stuff_tp` 的变量。
3. 将上述 `food_stuff_tp` 元组更改为 `food_stuff_lt` 列表。
4. 从 `food_stuff_tp` 元组或 `food_stuff_lt` 列表中切出中间的项目或项目。
5. 从 `food_staff_lt` 列表中切出前三个项目和最后三个项目。
6. 完全删除 `food_staff_tp` 元组。
7. 检查元组中是否存在项目：

- 检查 'Estonia' 是否是北欧国家。

- 检查 'Iceland' 是否是北欧国家。

  ```python
  nordic_countries = ('Denmark', 'Finland','Iceland', 'Norway', 'Sweden')
  ```
