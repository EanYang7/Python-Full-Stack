# 24 统计学Statistics

## 用于统计分析的Python

## 统计学

统计学是一门研究数据的**收集**、**组织**、**展示**、**分析**、**解释**和**呈现**的学科。
统计学是数学的一个分支，被推荐作为数据科学和机器学习的先决条件。统计学是一个非常广泛的领域，但在本节中我们只关注最相关的部分。完成这个挑战后，你可以进一步发展成为网络开发、数据分析、机器学习和数据科学的专家。无论你选择哪条道路，你都将在职业生涯的某个阶段获得数据，而一些统计知识将有助于你基于数据做出决策，正如所说的"数据告诉我们"。

## 数据

什么是数据？数据是为了某种目的而收集和翻译的一组字符，通常用于分析。它可以是任何字符，包括文本和数字、图片、声音或视频。如果数据没有放入上下文中，对人类或计算机来说都没有意义。要从数据中获取信息，我们需要使用不同的工具来处理数据。

数据分析、数据科学或机器学习的工作流程始于数据。数据可以来自某些数据源或可以创建。有结构化和非结构化数据。

数据可以以小或大的格式找到。大多数数据类型在文件处理部分都有涵盖。

## 统计模块

Python的**statistics**模块提供了计算数值数据的数学统计量的函数。该模块的目的不是与第三方库（如NumPy、SciPy）或面向专业统计学家的专业统计包（如Minitab、SAS和Matlab）竞争。它旨在满足图形和科学计算器的水平需求。

# NumPy

在第一部分中，我们将Python定义为一种出色的通用编程语言，但在使用其他流行的库（如NumPy、SciPy、matplotlib、pandas等）的帮助下，它变成了一个强大的科学计算环境。

NumPy是Python中用于科学计算的核心库。它提供了高性能的多维数组对象和处理数组的工具。

到目前为止，我们一直在使用vscode，但从现在开始，我建议使用Jupyter Notebook。要访问Jupyter Notebook，让我们安装[anaconda](https://www.anaconda.com/)。如果您使用anaconda，大多数常见的包都已包含在内，无需安装包。

```sh
asabeneh@Asabeneh:~/Desktop/30DaysOfPython$ pip install numpy
```

## 导入NumPy

如果您喜欢[Jupyter Notebook](https://github.com/Asabeneh/data-science-for-everyone/blob/master/numpy/numpy.ipynb)：

```py
    # 如何导入numpy
    import numpy as np
    # 如何检查numpy包的版本
    print('numpy:', np.__version__)
    # 检查可用的方法
    print(dir(np))
```

## 使用NumPy创建数组

### 创建整数型NumPy数组

```py
    # 创建Python列表
    python_list = [1,2,3,4,5]

    # 检查数据类型
    print('Type:', type (python_list)) # <class 'list'>
    #
    print(python_list) # [1, 2, 3, 4, 5]

    two_dimensional_list = [[0,1,2], [3,4,5], [6,7,8]]

    print(two_dimensional_list)  # [[0, 1, 2], [3, 4, 5], [6, 7, 8]]

    # 从Python列表创建NumPy（数值Python）数组

    numpy_array_from_list = np.array(python_list)
    print(type (numpy_array_from_list))   # <class 'numpy.ndarray'>
    print(numpy_array_from_list) # array([1, 2, 3, 4, 5])
```

### 创建浮点数型NumPy数组

从带有浮点数据类型参数的列表创建浮点数型NumPy数组

```py
    # Python列表
    python_list = [1,2,3,4,5]

    numy_array_from_list2 = np.array(python_list, dtype=float)
    print(numy_array_from_list2) # array([1., 2., 3., 4., 5.])
```

### 创建布尔型NumPy数组

从列表创建布尔型NumPy数组

```py
    numpy_bool_array = np.array([0, 1, -1, 0, 0], dtype=bool)
    print(numpy_bool_array) # array([False,  True,  True, False, False])
```

### 使用NumPy创建多维数组

NumPy数组可以具有一个或多个行和列

```py
    two_dimensional_list = [[0,1,2], [3,4,5], [6,7,8]]
    numpy_two_dimensional_list = np.array(two_dimensional_list)
    print(type (numpy_two_dimensional_list))
    print(numpy_two_dimensional_list)
```

```sh
    <class 'numpy.ndarray'>
    [[0 1 2]
     [3 4 5]
     [6 7 8]]
```

### 将NumPy数组转换为列表

```python
# 我们可以始终使用tolist()将数组转换回Python列表。
np_to_list = numpy_array_from_list.tolist()
print(type (np_to_list))
print('一维数组:', np_to_list)
print('二维数组: ', numpy_two_dimensional_list.tolist())
```

```sh
    <class 'list'>
    一维数组: [1, 2, 3, 4, 5]
    二维数组:  [[0, 1, 2], [3, 4, 5], [6, 7, 8]]
```

### 从元组创建NumPy数组

```py
# 从元组创建NumPy数组
# 在Python中创建元组
python_tuple = (1,2,3,4,5)
print(type (python_tuple)) # <class 'tuple'>
print('python_tuple: ', python_tuple) # python_tuple:  (1, 2, 3, 4, 5)

numpy_array_from_tuple = np.array(python_tuple)
print(type (numpy_array_from_tuple)) # <class 'numpy.ndarray'>
print('numpy_array_from_tuple: ', numpy_array_from_tuple) # numpy_array_from_tuple:  [1 2 3 4 5]
```

### NumPy数组的形状

形状方法以元组形式提供数组的形状。第一个是行数，第二个是列数。如果数组只有一维，它将返回数组的大小。

```py
    nums = np.array([1, 2, 3, 4, 5])
    print(nums)
    print('nums的形状: ', nums.shape)
    print(numpy_two_dimensional_list)
    print('numpy_two_dimensional_list的形状: ', numpy_two_dimensional_list.shape)
    three_by_four_array = np.array([[0, 1, 2, 3],
        [4,5,6,7],
        [8,9,10, 11]])
    print(three_by_four_array.shape)
```

```sh
    [1 2 3 4 5]
    nums的形状:  (5,)
    [[0 1 2]
     [3 4 5]
     [6 7 8]]
    numpy_two_dimensional_list的形状:  (3, 3)
    (3, 4)
```

### NumPy数组的数据类型

数据类型的类型：str、int、float、complex、bool、list、None

```py
int_lists = [-3, -2, -1, 0, 1, 2,3]
int_array = np.array(int_lists)
float_array = np.array(int_lists, dtype=float)

print(int_array)
print(int_array.dtype)
print(float_array)
print(float_array.dtype)
```

```sh
    [-3 -2 -1  0  1  2  3]
    int64
    [-3. -2. -1.  0.  1.  2.  3

.]
    float64
```

### NumPy数组的大小

在NumPy中，要知道NumPy数组列表中的项数，我们使用size

```py
numpy_array_from_list = np.array([1, 2, 3, 4, 5])
two_dimensional_list = np.array([[0, 1, 2],
                              [3, 4, 5],
                              [6, 7, 8]])

print('大小:', numpy_array_from_list.size) # 5
print('大小:', two_dimensional_list.size)  # 9

```

```sh
    大小: 5
    大小: 9
```

## 使用NumPy进行数学运算

NumPy数组与Python列表不完全相同。在Python列表中进行数学运算时，我们必须循环遍历项目，但NumPy可以在不循环的情况下执行任何数学运算。

数学运算：

- 加法（+）
- 减法（-）
- 乘法（*）
- 除法（/）
- 模运算（%）
- 地板除法（//）
- 指数运算（**）

### 加法

```py
# 数学操作
# 加法
numpy_array_from_list = np.array([1, 2, 3, 4, 5])
print('原始数组：', numpy_array_from_list)
ten_plus_original = numpy_array_from_list  + 10
print(ten_plus_original)

```

```sh
    原始数组： [1 2 3 4 5]
    [11 12 13 14 15]
```

### 减法

```python
# 减法
numpy_array_from_list = np.array([1, 2, 3, 4, 5])
print('原始数组：', numpy_array_from_list)
ten_minus_original = numpy_array_from_list  - 10
print(ten_minus_original)
```

```sh
    原始数组： [1 2 3 4 5]
    [-9 -8 -7 -6 -5]
```

### 乘法

```python
# 乘法
numpy_array_from_list = np.array([1, 2, 3, 4, 5])
print('原始数组：', numpy_array_from_list)
ten_times_original = numpy_array_from_list * 10
print(ten_times_original)
```

```sh
    原始数组： [1 2 3 4 5]
    [10 20 30 40 50]
```

### 除法

```python
# 除法
numpy_array_from_list = np.array([1, 2, 3, 4, 5])
print('原始数组：', numpy_array_from_list)
ten_times_original = numpy_array_from_list / 10
print(ten_times_original)
```

```sh
    原始数组： [1 2 3 4 5]
    [0.1 0.2 0.3 0.4 0.5]
```

### 取模

```python
# 取模; 找到余数
numpy_array_from_list = np.array([1, 2, 3, 4, 5])
print('原始数组：', numpy_array_from_list)
ten_times_original = numpy_array_from_list % 3
print(ten_times_original)
```

```sh
    原始数组： [1 2 3 4 5]
    [1 2 0 1 2]
```

### 地板除法

```py
# 地板除法：除法结果没有余数
numpy_array_from_list = np.array([1, 2, 3, 4, 5])
print('原始数组：', numpy_array_from_list)
ten_times_original = numpy_array_from_list // 10
print(ten_times_original)
```

### 指数

```py
# 指数是找到另一个数的幂：
numpy_array_from_list = np.array([1, 2, 3, 4, 5])
print('原始数组：', numpy_array_from_list)
ten_times_original = numpy_array_from_list  ** 2
print(ten_times_original)
```

```sh
    原始数组： [1 2 3 4 5]
    [ 1  4  9 16 25]
```

## 检查数据类型

```py
#整数、浮点数
numpy_int_arr = np.array([1,2,3,4])
numpy_float_arr = np.array([1.1, 2.0,3.2])
numpy_bool_arr = np.array([-3, -2, 0, 1,2,3], dtype='bool')

print(numpy_int_arr.dtype)
print(numpy_float_arr.dtype)
print(numpy_bool_arr.dtype)
```

```sh
    int64
    float64
    bool
```

### 转换类型

我们可以转换numpy数组的数据类型

1. 整数转浮点数

```py
numpy_int_arr = np.array([1,2,3,4], dtype = 'float')
numpy_int_arr
```

    array([1., 2., 3., 4.])

2. 浮点数转整数

```py
numpy_int_arr = np.array([1., 2., 3., 4.], dtype = 'int')
numpy_int_arr
```

```sh
    array([1, 2, 3, 4])
```

3. 整数转布尔值

```py
np.array([-3, -2, 0, 1,2,3], dtype='bool')

```

```sh
    array([ True,  True, False,  True,  True,  True])
```

4. 整数转字符串

```py
numpy_float_list.astype('int').astype('str')
```

```sh
    array(['1', '2', '3'], dtype='<U21')
```

## 多维数组

```py
# 2维数组
two_dimension_array = np.array([(1,2,3),(4,5,6), (7,8,9)])
print(type (two_dimension_array))
print(two_dimension_array)
print('形状：', two_dimension_array.shape)
print('大小:', two_dimension_array.size)
print('数据类型:', two_dimension_array.dtype)
```

```sh
    <class 'numpy.ndarray'>
    [[1 2 3]
     [4 5 6]
     [7 8 9]]
    形状： (3, 3)
    大小: 9
    数据类型: int64
```

### 从numpy数组获取项目

```py
# 2维数组
two_dimension_array = np.array([[1,2,3],[4,5,6], [7,8,9]])
first_row = two_dimension_array[0]
second_row = two_dimension_array[1]
third_row = two_dimension_array[2]
print('第一行:', first_row)
print('第二行:', second_row)
print('第三行: ', third_row)
```

```sh
    第一行: [1 2 3]
    第二行: [4 5 6]
    第三行:  [7 8 9]
```

```py
first_column= two_dimension_array[:,0]
second_column = two_dimension_array[:,1]
third_column = two_dimension_array[:,2]
print('第一列:', first_column)
print('第二列:', second_column)
print('第三列: ', third_column)
print(two_dimension_array)

```

```sh
    第一列: [1 4 7]
    第二列: [2 5 8]
    第三列:  [3 6 9]
    [[1 2 3]
     [4 5 6]
     [7 8 9]]
```

## Numpy数组切片

在numpy中切片类似于python列表中的切片

```py
two_dimension_array = np.array([[1,2,3],[4,5,6], [7,8,9]])
first_two_rows_and_columns = two_dimension_array[0:2, 0:2]
print(first_two_rows_and_columns)
```

```sh
    [[1 2]
     [4 5]]
```

### 如何反转行和整个数组？

```py
two_dimension_array[::]
```

```sh
    array([[1, 2, 3],
           [4, 5, 6],
           [7, 8, 9]])
```

### 反转行和列的位置

```py
    two_dimension_array = np.array([[1,2,3],[4,5,6], [7,8,9]])
    two_dimension_array[::-1,::-1]
```

```sh
    array([[9, 8, 7],
           [6, 5, 4],
           [3, 2, 1]])
```

## 如何表示缺失值？

```python
    print(two_dimension_array)
    two_dimension_array[1,1] = 55
    two_dimension_array[1,2] =44
    print(two_dimension_array)
```

```sh
    [[1 2 3]
     [4 5 6]
     [7 8 9]]
    [[ 1  2  3]
     [ 4 55 44]
     [ 7  8  9]]
```

```py
    # Numpy Zeroes
    # numpy.zeros(shape, dtype=float, order='C')
    numpy_zeroes = np.zeros((3,3),dtype=int,order='C')
    numpy_zeroes
```

```sh
    array([[0, 0, 0],
           [0, 0, 0],
           [0, 0, 0]])
```

```py
# Numpy Zeroes
numpy_ones = np.ones((3,3),dtype=int,order='C')
print(numpy_ones)
```

```sh
    [[1 1 1]
     [1 1 1]
     [1 1 1]]
```

```py
twoes = numpy_ones * 2
```

```py
# 重塑
# numpy.reshape(), numpy.flatten()
first_shape  = np.array([(1,2,3), (4,5,6)])
print(first_shape)
reshaped = first_shape.reshape(3,2)
print(reshaped)

```

```sh
    [[1 2 3]
     [4 5 6]]
    [[1 2]
     [3 4]
     [5 6]]
```

```py
flattened = reshaped.flatten()
flattened
```

```sh
    array([1, 2, 3, 4, 5, 6])
```

```py
    ## 水平堆叠
    np_list_one = np.array([1,2,3])
    np_list_two = np.array([4,5,6])

    print(np_list_one + np_list_two)

    print('Horizontal Append:', np.hstack((np_list_one, np_list_two)))
```

```sh
    [5 7 9]
    水平附加: [1 2 3 4 5 6]
```

```py
    ## 垂直堆叠
    print('Vertical Append:', np.vstack((np_list_one, np_list_two)))
```

```sh
    垂直附加: [[1 2 3]
     [4 5 6]]
```

#### 生成随机数

```py
    # 生成随机浮点数
    random_float = np.random.random()
    random_float
```

```sh
    0.018929887384753874
```

```py
    # 生成随机浮点数
    random_floats = np.random.random(5)
    random_floats
```

```sh
    array([0.26392192, 0.35842215, 0.87908478, 0.41902195, 0.78926418])
```

```py
    # 生成0到10之间的随机整数

    random_int = np.random.randint(0, 11)
    random_int
```

```sh
    4
```

```py
    # 生成2到11之间的随机整数，并创建一个一维数组
    random_int = np.random.randint(2,10, size=4)
    random_int
```

```sh
    array([8, 8, 8, 2])
```

```py
    # 生成0到10之间的随机整数
    random_int = np.random.randint(2,10, size=(3,3))
    random_int
```

```sh
    array([[3, 5, 3],
           [7, 3, 6],
           [2, 3, 3]])
```

### 生成随机数

```py
    # np.random.normal(mu, sigma, size)
    normal_array = np.random.normal(79, 15, 80)
    normal_array

```

```sh
    array([ 89.49990595,  82.06056961, 107.21445842,  38.69307086,
            47.85259157,  93.07381061,  76.40724259,  78.55675184,
            72.17358173,  47.9888899 ,  65.10370622,  76.29696568,
            95.58234254,  68.14897213,  38.75862686, 122.5587927 ,
            67.0762565 ,  95.73990864,  81.97454563,  92.54264805,
            59.37035153,  

 77.76828101,  52.30752166,  64.43109931,
            62.63695351,  90.04616138,  75.70009094,  49.87586877,
            80.22002414,  68.56708848,  76.27791052,  67.24343975,
            81.86363935,  78.22703433, 102.85737041,  65.15700341,
            84.87033426,  76.7569997 ,  64.61321853,  67.37244562,
            74.4068773 ,  58.65119655,  71.66488727,  53.42458179,
            70.26872028,  60.96588544,  83.56129414,  72.14255326,
            81.00787609,  71.81264853,  72.64168853,  86.56608717,
            94.94667321,  82.32676973,  70.5165446 ,  85.43061003,
            72.45526212,  87.34681775,  87.69911217, 103.02831489,
            75.28598596,  67.17806893,  92.41274447, 101.06662611,
            87.70013935,  70.73980645,  46.40368207,  50.17947092,
            61.75618542,  90.26191397,  78.63968639,  70.84550744,
            88.91826581, 103.91474733,  66.3064638 ,  79.49726264,
            70.81087439,  83.90130623,  87.58555972,  59.95462521])
```

## Numpy和统计

```py
import matplotlib.pyplot as plt
import seaborn as sns
sns.set()
plt.hist(normal_array, color="grey", bins=50)
```

```sh
    (array([2., 0., 0., 0., 1., 2., 2., 0., 2., 0., 0., 1., 2., 2., 1., 4., 3.,
            4., 2., 7., 2., 2., 5., 4., 2., 4., 3., 2., 1., 5., 3., 0., 3., 2.,
            1., 0., 0., 1., 3., 0., 1., 0., 0., 0., 0., 0., 0., 0., 0., 1.]),
     array([ 38.69307086,  40.37038529,  42.04769973,  43.72501417,
             45.4023286 ,  47.07964304,  48.75695748,  50.43427191,
             52.11158635,  53.78890079,  55.46621523,  57.14352966,
             58.8208441 ,  60.49815854,  62.17547297,  63.85278741,
             65.53010185,  67.20741628,  68.88473072,  70.56204516,
             72.23935959,  73.91667403,  75.59398847,  77.27130291,
             78.94861734,  80.62593178,  82.30324622,  83.98056065,
             85.65787509,  87.33518953,  89.01250396,  90.6898184 ,
             92.36713284,  94.04444727,  95.72176171,  97.39907615,
             99.07639058, 100.75370502, 102.43101946, 104.1083339 ,
            105.78564833, 107.46296277, 109.14027721, 110.81759164,
            112.49490608, 114.17222052, 115.84953495, 117.52684939,
            119.20416383, 120.88147826, 122.5587927 ]),
     <a list of 50 Patch objects>)
```

### Numpy矩阵

```py
four_by_four_matrix = np.matrix(np.ones((4,4), dtype=float))
```

```py
four_by_four_matrix
```

```sh
matrix([[1., 1., 1., 1.],
            [1., 1., 1., 1.],
            [1., 1., 1., 1.],
            [1., 1., 1., 1.]])
```

```py
np.asarray(four_by_four_matrix)[2] = 2
four_by_four_matrix
```

```sh
matrix([[1., 1., 1., 1.],
            [1., 1., 1., 1.],
            [2., 2., 2., 2.],
            [1., 1., 1., 1.]])
```

### Numpy numpy.arange()

#### 什么是Arrange？

有时，您希望在定义的间隔内均匀间隔的值。例如，您希望在1到10之间创建值；您可以使用numpy.arange()函数

```py
# 使用range(starting, stop, step)创建列表
lst = range(0, 11, 2)
lst
```

```python
range(0, 11, 2)
```

```python
for l in lst:
    print(l)
```

```sh 0
    2
    4
    6
    8
    10
```

```py
# 类似于range arange numpy.arange(start, stop, step)
whole_numbers = np.arange(0, 20, 1)
whole_numbers
```

```sh
array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13, 14, 15, 16,
           17, 18, 19])
```



```py
natural_numbers = np.arange(1, 20, 1)
natural_numbers
```

```py
odd_numbers = np.arange(1, 20, 2)
odd_numbers
```

```sh
    array([ 1,  3,  5,  7,  9, 11, 13, 15, 17, 19])
```

```py
even_numbers = np.arange(2, 20, 2)
even_numbers
```

```sh
    array([ 2,  4,  6,  8, 10, 12, 14, 16, 18])
```

### 使用linspace创建数字序列

```py
# numpy.linspace()
# numpy.logspace() in Python with Example
# 例如，它可以用于从1到5创建10个均匀间隔的值。
np.linspace(1.0, 5.0, num=10)
```

```sh
    array([1.        , 1.44444444, 1.88888889, 2.33333333, 2.77777778,
           3.22222222, 3.66666667, 4.11111111, 4.55555556, 5.        ])
```

```py
# 不包括间隔中的最后一个值
np.linspace(1.0, 5.0, num=5, endpoint=False)
```

```
array([1. , 1.8, 2.6, 3.4, 4.2])
```

```py
# LogSpace
# LogSpace返回在对数尺度上均匀间隔的数字。Logspace具有与np.linspace相同的参数。

# 语法：

# numpy.logspace(start, stop, num, endpoint)

np.logspace(2, 4.0, num=4)
```

```sh
array([  100.        ,   464.15888336,  2154.43469003, 10000.        ])
```

```py
# 检查数组的大小
x = np.array([1,2,3], dtype=np.complex128)
```

```py
x
```

```sh
    array([1.+0.j, 2.+0.j, 3.+0.j])
```

```py
x.itemsize
```

```sh
16
```

```py
# 在Python中索引和切片NumPy数组
np_list = np.array([(1,2,3), (4,5,6)])
np_list

```

```sh
    array([[1, 2, 3],
           [4, 5, 6]])
```

```py
print('第一行: ', np_list[0])
print('第二行: ', np_list[1])

```

```sh
    第一行:  [1 2 3]
    第二行:  [4 5 6]
```

```p
print('第一列: ', np_list[:,0])
print('第二列: ', np_list[:,1])
print('第三列: ', np_list[:,2])

```

```sh
    第一列:  [1 4]
    第二列:  [2 5]
    第三列:  [3 6]
```

### NumPy统计函数示例

NumPy具有用于从数组中查找最小值、最大值、均值、中位数、百分位数、标准差和方差等的非常有用的统计函数。
这些函数如下所示：

统计函数
Numpy配备了如下所示的强大的统计函数

- Numpy函数
  - Min np.min()
  - Max np.max()
  - Mean np.mean()
  - Median np.median()
  - Variance
  - Percentile
  - Standard deviation np.std()

```python
np_normal_dis = np.random.normal(5, 0.5, 100)
np_normal_dis
## 最小值、最大值、均值、中位数、标准差
print('最小值: ', two_dimension_array.min())
print('最大值: ', two_dimension_array.max())
print('均值: ',two_dimension_array.mean())
# print('中位数: ', two_dimension_array.median())
print('标准差: ', two_dimension_array.std())
```

```python
最小值:  1
最大值:  55
均值:  14.777777777777779
标准差:  18.913709183069525
```

```python
print(two_dimension_array)
print('最小的列: ', np.amin(two_dimension_array,axis=0))
print('最大的列: ', np.amax(two_dimension_array,axis=0))
print('=== 行 ==')
print('最小的行: ', np.amin(two_dimension_array,axis=1))
print('最大的行: ', np.amax(two_dimension_array,axis=1))
```

```sh
    [[ 1  2  3]
     [ 4 55 44]
     [ 7  8  9]]
    最小的列:  [1 2 3]
    最大的列:  [ 7 55 44]
    === 行 ==
    最小的行:  [1 4 7]
    最大的行:  [ 3 55  9]
```

### 如何创建重复的序列？

```python
a = [1,2,3]

# 整个 'a' 重复两次
print('Tile:   ', np.tile(a, 2))

# 每个元素 'a' 重复两次
print('Repeat: ', np.repeat(a, 2))

```

    Tile:    [1 2 3 1 2 3]
    Repeat:  [1 1 2 2 3 3]

### 如何生成随机数？

```python
# 在[0,1)之间生成一个随机数
one_random_num = np.random.random()
one_random_in = np.random
print(one_random_num)
```

    0.6149403282678213

```python
0.4763968133790438
```

    0.4763968133790438

```python
# 在形状为2,3的[0,1)之间生成随机数
r = np.random.random(size=[2,3])
print(r)
```

    [[0.13031737 0.4429537  0.1129527 ]
     [0.76811539 0.88256594 0.6754075 ]]

```python
print(np.random.choice(['a', 'e', 'i', 'o', 'u'], size=10))
```

    ['u' 'o' 'o' 'i' 'e' 'e' 'u' 'o' 'u' 'a']

```python
['i' 'u' 'e' 'o' 'a' 'i' 'e' 'u' 'o' 'i']
```

    ['iueoaieuoi']

```python
## 在形状为2,2的[0, 1]之间生成随机数
rand = np.random.rand(2,2)
rand
```

    array([[0.97992598, 0.79642484],
               [0.65263629, 0.55763145]])

```python
rand2 = np.random.randn(2,2)
rand2

```

    array([[ 1.65593322, -0.52326621],
           [ 0.39071179, -2.03649407]])

```python
# 在[0, 10)之间生成形状为2,5的随机整数
rand_int = np.random.randint(0, 10, size=[5,3])
rand_int
```

    array([[0, 7, 5],
           [4, 1, 4],
           [3, 5, 3],
           [4, 3, 8],
           [4, 6, 7]])

```py
from scipy import stats
np_normal_dis = np.random.normal(5, 0.5, 1000) # 均值、标准差、样本数
np_normal_dis
## 最小值、最大值、均值、中位数、众数、标准差
print('最小值: ', np.min(np_normal_dis))
print('最大值: ', np.max(np_normal_dis))
print('均值: ', np.mean(np_normal_dis))
print('中位数: ', np.median(np_normal_dis))
print('众数: ', stats.mode(np_normal_dis))
print('标准差: ', np.std(np_normal_dis))
```

```sh
    最小值:  3.557811005458804
    最大值:  6.876317743643499
    均值:  5.035832048106663
    中位数:  5.020161980441937
    众数:  ModeResult(mode=array([3.55781101]), count=array([1]))
    标准差:  0.489682424165213

```

```python
plt.hist(np_normal_dis, color="grey", bins=21)
plt.show()
```

![png](../test_files/test_121_0.png)

```python
# numpy.dot()：使用Numpy计算Python中的点积
# 点积
# Numpy是进行矩阵计算的强大库。例如，您可以使用np.dot计算点积

# 语法

# numpy.dot(x, y, out=None)
```

### 线性代数

1. 点积

```python
## 线性代数
### 点积：两个数组的乘积
f = np.array([1,2,3])
g = np.array([4,5,3])
### 1*4+2*5 + 3*6
np.dot(f, g)  # 23
```

### 使用np.matmul()进行NumPy矩阵乘法

```python
### Matmul：两个数组的矩阵乘积
h = [[1,2],[3,4]]
i = [[5,6],[7,8]]
### 1*5+2*7 = 19
np.matmul(h, i)
```

```sh
    array([[19, 22],
           [43, 50]])

```

```py
## 行列式 2*2 矩阵
### 5*8-7*6np.linalg.det(i)
```

```python
np.linalg.det(i)
```

```
-1.999999999999999
```

```python
Z = np.zeros((8,8))
Z[1::2,::2] = 1
Z[::2,1::2] = 1
```

```python
Z
```

```
array([[0., 1., 0., 1., 0., 1., 0., 1.],
       [1., 0., 1., 0., 1., 0., 1., 0.],
       [0., 1., 0., 1., 0., 1., 0., 1.],
       [1., 0., 1., 0., 1., 0., 1., 0.],
       [0., 1., 0., 1., 0., 1., 0., 1.],
       [1., 0., 1., 0., 1., 0., 1., 0.],
       [0., 1., 0., 1., 0., 1., 0., 1.],
       [1., 0., 1., 0., 1., 0., 1., 0.]])
```

```python
new_list = [ x + 2 for x in range(0, 11)]
```

```python
new_list
```

```
[2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]
```

```python
[2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]
```

```
[2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]
```

```python
np_arr = np.array(range(0, 11))
np_arr + 2
```

array([ 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12])

我们使用线性方程来描述具有线性关系的量。让我们看下面的例子：

```python
temp = np.array([1,2,3,4,5])
pressure = temp * 2 + 5
pressure
```

array([ 7, 9, 11, 13, 15])

```python
plt.plot(temp,pressure)
plt.xlabel('摄氏温度')
plt.ylabel('大气压力')
plt.title('温度 vs 压力')
plt.xticks(np.arange(0, 6, step=0.5))
plt.show()
```

![png](../test_files/test_141_0.png)

使用numpy绘制高斯正态分布。如下所示，numpy可以生成随机数。要创建随机样本，我们需要均值(mu)、标准差(sigma)和数据点的数量。

```python
mu = 28
sigma = 15
samples = 100000

x = np.random.normal(mu, sigma, samples)
ax = sns.distplot(x);
ax.set(xlabel="x", ylabel='y')
plt.show()
```

![png](../test_files/test_143_0.png)

# 总结

总结一下，与Python列表的主要区别有：

1. 数组支持矢量化操作，而列表不支持。
1. 一旦创建了数组，就不能改变其大小。您将不得不创建一个新数组或覆盖现有数组。
1. 每个数组只有一个dtype。其中的所有项都应该是该dtype。
1. 等效的numpy数组占用的空间比python列表的列表少得多。
1. numpy数组支持布尔索引。
