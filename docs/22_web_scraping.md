# 22 网络爬虫

## Web爬取

### 什么是网络爬虫

互联网上充满了大量的数据，可以用于不同的目的。为了收集这些数据，我们需要知道如何从网站上抓取数据。

Web爬取是从网站上提取和收集数据并将其存储在本地计算机或数据库中的过程。

在这一部分中，我们将使用beautifulsoup和requests包来进行数据抓取。我们使用的包版本是beautifulsoup 4。

要开始从网站上抓取数据，您需要 _requests_，_beautifulsoup4_ 和一个 _网站_。

```sh
pip install requests
pip install beautifulsoup4
```

要从网站上抓取数据，需要基本了解HTML标记和CSS选择器。我们使用HTML标记、class类/id来定位网站上的内容。
让我们导入requests和BeautifulSoup模块

```py
import requests
from bs4 import BeautifulSoup
```

让我们为要抓取的网站声明url变量。

```py
import requests
from bs4 import BeautifulSoup
url = 'https://archive.ics.uci.edu/ml/datasets.php'

# 让我们使用requests的get方法来从url获取数据

response = requests.get(url)
# 检查状态
status = response.status_code
print(status) # 200表示获取成功
```

```sh
200
```

使用beautifulSoup来解析页面中的内容

```py
import requests
from bs4 import BeautifulSoup
url = 'https://archive.ics.uci.edu/ml/datasets.php'

response = requests.get(url)
content = response.content # 获取网站上的所有内容
soup = BeautifulSoup(content, 'html.parser') # beautiful soup将会给我们一个解析的机会
print(soup.title) # <title>UCI Machine Learning Repository: Data Sets</title>
print(soup.title.get_text()) # UCI Machine Learning Repository: Data Sets
print(soup.body) # 给出了整个网站的页面
print(response.status_code)

tables = soup.find_all('table', {'cellpadding':'3'})
# 我们定位了具有cellpadding属性值为3的表格
# 我们可以使用id、class或HTML标记来选择，更多信息请查看beautifulsoup文档
table = tables[0] # 结果是一个列表，我们从中取出数据
for td in table.find('tr').find_all('td'):
    print(td.text)
```

如果您运行这段代码，您会看到提取只完成了一半。您可以继续进行，因为这是练习1的一部分。
有关参考，请查看[beautifulsoup文档](https://www.crummy.com/software/BeautifulSoup/bs4/doc/#quick-start)

## 💻 练习：第22天

1. 抓取以下网站的数据并将其存储为json文件（url = 'http://www.bu.edu/president/boston-university-facts-stats/'）。
2. 提取此网址中的表格（https://archive.ics.uci.edu/ml/datasets.php）并将其更改为json文件。
3. 抓取总统表格的数据并将其存储为json（https://en.wikipedia.org/wiki/List_of_presidents_of_the_United_States）。该表格结构不太规整，抓取可能需要很长时间。

