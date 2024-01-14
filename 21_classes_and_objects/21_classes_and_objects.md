# 21 类和对象

## 类和对象

Python是一种面向对象的编程语言。在Python中，一切都是对象，具有其属性和方法。程序中使用的数字、字符串、列表、字典、元组、集合等都是相应内置类的对象。我们通过创建类来创建对象。类似于对象构造函数或用于创建对象的“蓝图blueprint”。我们实例化一个类来创建一个对象。类定义了对象的属性和行为，而对象则表示类。

Python程序中的每个元素都是一个类的对象。
让我们来看看Python中的一切是否都是类：

```py
$ python
Python 3.9.6 (default, Jun 28 2021, 15:26:21)
[Clang 11.0.0 (clang-1100.0.33.8)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> num = 10
>>> type(num)
<class 'int'>
>>> string = 'string'
>>> type(string)
<class 'str'>
>>> boolean = True
>>> type(boolean)
<class 'bool'>
>>> lst = []
>>> type(lst)
<class 'list'>
>>> tpl = ()
>>> type(tpl)
<class 'tuple'>
>>> set1 = set()
>>> type(set1)
<class 'set'>
>>> dct = {}
>>> type(dct)
<class 'dict'>
```

### 创建一个类

要创建一个类，我们需要使用关键字**class**，后面跟着类的名称和冒号。类名称应该使用**CamelCase**。

```sh
# 语法
class ClassName:
  代码在这里
```

**示例：**

```py
class Person:
  pass
print(Person)
```

```sh
<__main__.Person object at 0x10804e510>
```

### 创建一个对象

我们可以通过调用类来创建一个对象。

```py
p = Person()
print(p)
```

### 类构造函数Class Constructor

在上面的示例中，我们从Person类创建了一个对象。然而，在实际应用中，没有构造函数的类实际上并不太有用。让我们使用构造函数函数来使我们的类更有用。与Java或JavaScript中的构造函数一样，Python也有一个内置的`__init__()`构造函数。`__init__()`构造函数具有`self`参数，这个参数是一个引用，指向当前类的实例（也就是对象）。
> `self`是一个习惯上用来表示对象自身的变量名，它允许我们在类的方法内部访问和操作对象的属性和方法。通过使用 `self`，我们可以在类的方法中访问当前实例的属性，这样可以确保方法操作的是调用它的对象的数据，而不是其他对象的数据。

**示例：**

```py
class Person:
      def __init__ (self, name):
        # self允许将参数附加到类
          self.name =name

p = Person('Ean')
print(p.name)
print(p)
```

```sh
# 输出
Ean
<__main__.Person object at 0x2abf46907e80>
```

让我们向构造函数添加更多参数。

```py
class Person:
      def __init__(self, firstname, lastname, age, country, city):
          self.firstname = firstname
          self.lastname = lastname
          self.age = age
          self.country = country
          self.city = city


p = Person('Asabeneh', 'Yetayeh', 250, '芬兰', '赫尔辛基')
print(p.firstname)
print(p.lastname)
print(p.age)
print(p.country)
print(p.city)
```

```sh
# 输出
Asabeneh
Yetayeh
250
Finland
Helsinki
```

### 对象方法

对象可以有方法。方法methods是属于对象的函数functions。

**示例：**

```py
class Person:
      def __init__(self, firstname, lastname, age, country, city):
          self.firstname = firstname
          self.lastname = lastname
          self.age = age
          self.country = country
          self.city = city
      def person_info(self):
        return f'{self.firstname} {self.lastname} is {self.age} years old. He lives in {self.city}, {self.country}'

p = Person('Asabeneh', 'Yetayeh', 250, '芬兰', '赫尔辛基')
print(p.person_info())
```

```sh
# 输出
Asabeneh Yetayeh is 250 years old. He lives in Helsinki, Finland
```

### 对象的默认方法

有时，您可能希望为对象方法设置默认值。如果我们在构造函数中为参数设置默认值，那么在不带参数调用或实例化类时，可以避免错误。让我们看看它是什么样子：

**示例：**

```py
class Person:
      def __init__(self, firstname='Asabeneh', lastname='Yetayeh', age=250, country='芬兰', city='赫尔辛基'):
          self.firstname = firstname
          self.lastname = lastname
          self.age = age
          self.country = country
          self.city = city

      def person_info(self):
        return f'{self.firstname} {self.lastname} is {self.age} years old. He lives in {self.city}, {self.country}.'

p1 = Person()
print(p1.person_info())
p2 = Person('John', 'Doe', 30, 'Nomanland', 'Noman city')
print(p2.person_info())
```

```sh
# 输出
Asabeneh Yetayeh is 250 years old. He lives in Helsinki, Finland.
John Doe is 30 years old. He lives in Noman city, Nomanland.
```

### 用于修改类默认值的方法

在下面的示例中，person类中所有的构造函数参数都有默认值。除此之外，我们还有skills参数，我们可以使用方法来访问它。让我们创建add_skill方法来将skills添加到技能skills中。

```py
class Person:
      def __init__(self, firstname='Asabeneh', lastname='Yetayeh', age=250, country='芬兰', city='赫尔辛基'):
          self.firstname = firstname
          self.lastname = lastname
          self.age = age
          self.country = country
          self.city = city
          self.skills = []

      def person_info(self):
        return f'{self.firstname} {self.lastname} is {self.age} years old. He lives in {self.city}, {self.country}.'
      def add_skill(self, skill):
          self.skills.append(skill)

p1 = Person()
print(p1.person_info())
p1.add_skill('HTML')
p1.add_skill('CSS')
p1.add_skill('JavaScript')
p2 = Person('John', 'Doe', 30, 'Nomanland', 'Noman city')
print(p2.person_info())
print(p1.skills)
print(p2.skills)
```

```sh
# 输出
Asabeneh Yetayeh is 250 years old. He lives in Helsinki, Finland.
John Doe is 30 years old. He lives in Noman city, Nomanland.
['HTML', 'CSS', 'JavaScript']
[]
```

### 继承Inheritance

使用继承，我们可以重用父类代码。继承允许我们定义一个类，该类继承自另一个或父类的所有方法和属性。父类parent或超类super或基类base是提供所有方法和属性的类。子类是从另一个或父类继承的类。
让我们通过继承person类来创建一个student类。

```py
class Student(Person):
    pass


s1 = Student('Eyob', 'Yetayeh', 30, '芬兰', '赫尔辛基')
s2 = Student('Lidiya', 'Teklemariam', 28, '芬兰', '埃斯波')
print(s1.person_info())
s1.add_skill('JavaScript')
s1.add_skill('React')
s1.add_skill('Python')
print(s1.skills)

print(s2.person_info())
s2.add_skill('Organizing')
s2.add_skill('Marketing')
s2.add_skill('Digital Marketing')
print(s2.skills)

```

```sh
输出
Eyob Yetayeh is 30 years old. He lives in Helsinki, Finland.
['JavaScript', 'React', 'Python']
Lidiya Teklemariam is 28 years old. He lives in Espoo, Finland.
['Organizing', 'Marketing', 'Digital Marketing']
```

我们没有在子类中调用`__init__()`构造函数。如果我们不调用它，那么我们仍然可以访问父类的所有属性。但是如果我们调用构造函数，我们可以通过调用`super()`来访问父类属性。

我们可以向子类添加一个新方法，也可以通过在子类中创建相同的方法名来覆盖父类方法。当我们添加`__init__()`函数时，子类将不再继承父类的`__init__()`功能。

```python
class Student(Person):
    def __init__ (self, firstname='Asabeneh', lastname='Yetayeh',age=250, country='Finland', city='Helsinki', gender='male'):
        self.gender = gender
        super().__init__(firstname, lastname,age, country, city)
    def person_info(self):
        gender = 'He' if self.gender =='male' else 'She'
        return f'{self.firstname} {self.lastname} is {self.age} years old. {gender} lives in {self.city}, {self.country}.'

s1 = Student('Eyob', 'Yetayeh', 30, 'Finland', 'Helsinki','male')
s2 = Student('Lidiya', 'Teklemariam', 28, 'Finland', 'Espoo', 'female')
print(s1.person_info())
s1.add_skill('JavaScript')
s1.add_skill('React')
s1.add_skill('Python')
print(s1.skills)

print(s2.person_info())
s2.add_skill('Organizing')
s2.add_skill('Marketing')
s2.add_skill('Digital Marketing')
print(s2.skills)
```

```
Eyob Yetayeh is 30 years old. He lives in Helsinki, Finland.
['JavaScript', 'React', 'Python']
Lidiya Teklemariam is 28 years old. She lives in Espoo, Finland.
['Organizing', 'Marketing', 'Digital Marketing']
```

我们可以使用`super()`内置函数或父名称Person来自动从其父类继承方法和属性。在上面的示例中，我们重写了父类方法。子类方法具有不同的功能，它可以识别性别是男性还是女性，并分配适当的代词(He/She)。

🌕现在，您已经具备了编程的超能力。现在为您的大脑和肌肉做一些锻炼。

## 💻 练习：第21天

### 练习：Level 1

1. Python有一个名为 _statistics_ 的模块，我们可以使用这个模块来进行所有的统计计算。但是，为了学习如何编写函数并重复使用函数，让我们尝试开发一个程序，用于计算样本的中心趋势测量(均值、中位数、众数)和变异性测量(范围、方差、标准差)。除了这些测量，还要找到样本的最小值、最大值、计数、百分位数和频率分布。您可以创建一个名为Statistics的类，并将所有执行统计计算的函数创建为Statistics类的方法。检查下面的输出。

```py
ages = [31, 26, 34, 37, 27, 26, 32, 32, 26, 27, 27, 24, 32, 33, 27, 25, 26, 38, 37, 31, 34, 24, 33, 29, 26]

print('Count:', data.count()) # 25
print('Sum: ', data.sum()) # 744
print('Min: ', data.min()) # 24
print('Max: ', data.max()) # 38
print('Range: ', data.range() # 14
print('Mean: ', data.mean()) # 30
print('Median: ', data.median()) # 29
print('Mode: ', data.mode()) # {'mode': 26, 'count': 5}
print('Standard Deviation: ', data.std()) # 4.2
print('Variance: ', data.var()) # 17.5
print('Frequency Distribution: ', data.freq_dist()) # [(20.0, 26), (16.0, 27), (12.0, 32), (8.0, 37), (8.0, 34), (8.0, 33), (8.0, 31), (8.0, 24), (4.0, 38), (4.0, 29), (4.0, 25)]
```

```sh
# 您的输出应该如下所示
print(data.describe())
Count: 25
Sum:  744
Min:  24
Max:  38
Range:  14
Mean:  30
Median:  29
Mode:  (26, 5)
Variance:  17.5
Standard Deviation:  4.2
Frequency Distribution: [(20.0, 26), (16.0, 27), (12.0, 32), (8.0, 37), (8.0, 34), (8.0, 33), (8.0, 31), (8.0, 24), (4.0, 38), (4.0, 29), (4.0, 25)]
```

### 练习：Level 2

1. 创建一个名为PersonAccount的类。它具有firstname、lastname、incomes、expenses属性，以及total_income、total_expense、account_info、add_income、add_expense和account_balance方法。收入是一组收入及其说明。同样，开支也是如此。