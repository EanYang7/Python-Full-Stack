

# 16 datetime

## Python *datetime*

Python有`datetime`模块来处理日期和时间。

```py
import datetime
print(dir(datetime))
['MAXYEAR', 'MINYEAR', '__builtins__', '__cached__', '__doc__', '__file__', '__loader__', '__name__', '__package__', '__spec__', 'date', 'datetime', 'datetime_CAPI', 'sys', 'time', 'timedelta', 'timezone', 'tzinfo']
```

使用dir或help内置命令可以查看特定模块中可用的函数。如您所见，datetime模块中有许多函数，但我们将关注`date`、`datetime`、`time`和`timedelta`。让我们逐个看看它们。

### 获取*datetime*信息

```py
from datetime import datetime
now = datetime.now()
print(now)                      # 2021-07-08 07:34:46.549883
day = now.day                   # 8
month = now.month               # 7
year = now.year                 # 2021
hour = now.hour                 # 7
minute = now.minute             # 38
second = now.second
timestamp = now.timestamp()
print(day, month, year, hour, minute)
print('timestamp', timestamp)
print(f'{day}/{month}/{year}, {hour}:{minute}')  # 8/7/2021, 7:38
```

时间戳或Unix时间戳是从1970年1月1日UTC开始经过的秒数。

### 使用*strftime*格式化日期输出

```py
from datetime import datetime
new_year = datetime(2020, 1, 1)
print(new_year)      # 2020-01-01 00:00:00
day = new_year.day
month = new_year.month
year = new_year.year
hour = new_year.hour
minute = new_year.minute
second = new_year.second
print(day, month, year, hour, minute) #1 1 2020 0 0
print(f'{day}/{month}/{year}, {hour}:{minute}')  # 1/1/2020, 0:0

```

使用*strftime*方法格式化日期时间，文档可以在[此处](https://strftime.org/)找到。

```py
from datetime import datetime
# 当前日期和时间
now = datetime.now()
t = now.strftime("%H:%M:%S")
print("time:", t)
time_one = now.strftime("%m/%d/%Y, %H:%M:%S")
# mm/dd/YY H:M:S 格式
print("time one:", time_one)
time_two = now.strftime("%d/%m/%Y, %H:%M:%S")
# dd/mm/YY H:M:S 格式
print("time two:", time_two)
```

```sh
time: 01:05:01
time one: 12/05/2019, 01:05:01
time two: 05/12/2019, 01:05:01
```

以下是我们用于格式化时间的所有_strftime_符号示例。

![strftime](./images/strftime.png)

### 使用*strptime*将字符串转换为时间

这里有一份[文档](https://www.programiz.com/python-programming/datetime/strptimet)可以帮助理解格式。

```py
from datetime import datetime
date_string = "5 December, 2019"
print("date_string =", date_string)
date_object = datetime.strptime(date_string, "%d %B, %Y")
print("date_object =", date_object)
```

```sh
date_string = 5 December, 2019
date_object = 2019-12-05 00:00:00
```

### 使用*datetime*中的*date*

```py
from datetime import date
d = date(2020, 1, 1)
print(d)   						   # 2020-01-01
print('Current date:', d.today())    # 2019-12-05
# 今天的日期对象
today = date.today()
print("Current year:", today.year)   # 2019
print("Current month:", today.month) # 12
print("Current day:", today.day)     # 5
```

### 使用time对象表示时间

```py
from datetime import time
# time(hour = 0, minute = 0, second = 0)
a = time()
print("a =", a)
# time(hour, minute and second)
b = time(10, 30, 50)
print("b =", b)
# time(hour, minute and second)
c = time(hour=10, minute=30, second=50)
print("c =", c)
# time(hour, minute, second, microsecond)
d = time(10, 30, 50, 200555)
print("d =", d)
```

输出  
a = 00:00:00  
b = 10:30:50  
c = 10:30:50  
d = 10:30:50.200555

### 计算两个时间点之间的时间差

```py
from datetime import date,datetime

today = date(year=2019, month=12, day=5)
new_year = date(year=2020, month=1, day=1)
time_left_for_newyear = new_year - today
# 距离新年还有: 27 天, 0:00:00
print('距离新年还有: ', time_left_for_newyear)

t1 = datetime(year = 2019, month = 12, day = 5, hour = 0, minute = 59, second = 0)
t2 = datetime(year = 2020, month = 1, day = 1, hour = 0, minute = 0, second = 0)
diff = t2 - t1
print('距离新年还有:', diff) # 距离新年还有: 26 天, 23: 01: 00
```

### 使用*timedelata*计算两个时间点之间的时间差

```py
from datetime import timedelta
t1 = timedelta(weeks=12, days=10, hours=4, seconds=20)
t2 = timedelta(days=7, hours=5, minutes=3, seconds=30)
t3 = t1 - t2
print("t3 =", t3)	# t3 = 86 days, 22:56:50
```

---

`timedelta` 是 Python 标准库中 `datetime` 模块中的一个类，用于表示时间间隔或持续时间。它允许您执行日期和时间上的算术运算，例如在日期上加上一段时间或计算两个日期之间的时间差。

`timedelta` 对象具有以下主要属性：
- `days`：表示天数的整数部分。
- `seconds`：表示秒数的整数部分。
- `microseconds`：表示微秒数的整数部分。
- `milliseconds`：表示毫秒数的整数部分。
- `minutes`：表示分钟数的整数部分。
- `hours`：表示小时数的整数部分。
- `weeks`：表示周数的整数部分。

您可以创建 `timedelta` 对象，然后使用它执行各种日期和时间的算术操作。例如，您可以将 `timedelta` 添加到日期或时间，计算两个日期之间的时间差，或者执行其他与时间间隔相关的操作。

以下是一些使用 `timedelta` 的示例：

```python
from datetime import timedelta

# 创建一个timedelta对象，表示5天
delta = timedelta(days=5)

# 当前日期
current_date = datetime.now().date()

# 计算5天后的日期
new_date = current_date + delta

print("当前日期:", current_date)
print("5天后的日期:", new_date)
```

`timedelta` 对象对于在程序中执行日期和时间的增减操作非常有用，它们允许您轻松进行时间计算和处理时间间隔。

## 💻 练习：第16天

1. 从datetime

模块获取当前的日期、月份、年份、小时、分钟和时间戳。
1. 使用以下格式格式化当前日期："％m/％d/％Y，％H：％M：％S"。
1. 今天是2019年12月5日。将这个时间字符串转换为时间。
1. 计算现在和新年之间的时间差。
1. 计算1970年1月1日与现在之间的时间差。
1. 思考一下，您可以使用datetime模块来做什么？例如：
   - 时间序列分析
   - 获取应用程序中任何活动的时间戳
   - 在博客上发布帖子