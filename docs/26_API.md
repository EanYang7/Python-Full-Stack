# 28 API


API代表应用程序编程接口Application Programming Interface。在本节中，我们将介绍的API类型是Web API。
Web API是定义的接口，通过这些接口，企业与使用其资产的应用程序之间进行交互，同时也是服务级别协议（Service Level Agreement,SLA），用于指定功能提供商并公开其API用户的服务路径或URL。

在Web开发的上下文中，API被定义为一组规范specifications，例如超文本传输协议（Hypertext Transfer Protocol,HTTP）请求消息，以及响应消息的结构定义，通常以XML或JavaScript对象表示法（JavaScript Object Notation,JSON）格式。

Web API已经从基于简单对象访问协议（Simple Object Access Protocol,SOAP）的Web服务和面向服务的体系结构（service-oriented architecture,SOA）转向了更直接的表现状态传输（representational state transfer,REST）样式的Web资源。

社交媒体服务、Web API使Web社区能够在社区和不同平台之间共享内容和数据。

使用API，可以在Web上动态创建的内容在多个位置上发布和更新。

例如，Twitter的REST API允许开发人员访问核心的Twitter数据，搜索API提供了与Twitter搜索和趋势数据交互的方法。

许多应用程序提供API端点endpoints。一些API的示例包括国家[API](https://restcountries.com/v3.1/all)，[猫品种API](https://api.thecatapi.com/v1/breeds)。

在本节中，我们将介绍一种使用HTTP请求方法来获取GET、放置PUT、发布POST和删除DELETE数据的RESTful API。

## 构建API

RESTful API是一种使用HTTP请求来获取、放置、发布和删除数据的应用程序编程接口(API)。每个具有CRUD（创建、读取、更新、删除）操作的应用程序都有一个用于创建数据、获取数据、更新数据或从数据库中删除数据的API。

要构建API，了解HTTP协议和HTTP请求和响应循环是很有帮助的。

## HTTP（超文本传输协议）

HTTP是客户端和服务器之间的一种已建立的通信协议。在这种情况下，客户端是浏览器，服务器是您访问数据的地方。HTTP是用于传递资源的网络协议，这些资源可以是万维网上的文件，无论是HTML文件、图像文件、查询结果、脚本还是其他文件类型。

浏览器是HTTP客户端，因为它发送请求到HTTP服务器（Web服务器），然后服务器将响应发送回客户端。

## HTTP的结构

HTTP使用客户端-服务器client-server模型。HTTP客户端打开连接并发送请求消息到HTTP服务器，HTTP服务器返回请求的资源的响应消息。当请求响应循环完成时，服务器关闭连接。

![HTTP请求响应循环](./images/http_request_response_cycle.png)

请求和响应消息的格式相似。两种类型的消息都有

- 初始行
- 零个或多个头行header lines
- 一个空行（即单独的CRLF）

??? note "CRLF是什么?"

    "CRLF" 表示回车符 (Carriage Return,CR) 和换行符 (Line Feed,LF) 的组合，通常以 "\r\n" 表示。在文本文件中，它表示一个空白行或换行符。回车符和换行符是控制字符，用于在文本中表示新的行。在不同的操作系统和文本编辑器中，行尾的表示方式可能会有所不同。

- 一个可选的消息主体（例如文件、查询数据或查询输出）

让我们通过访问此站点来查看请求和响应消息的示例:https://thirtydaysofpython-v1-final.herokuapp.com/。此站点已部署在Heroku免费dyno上，有时可能因请求量过大而无法正常工作。支持此工作以使服务器一直运行。

![请求和响应头](./images/request_response_header.png)

## 初始请求行（状态行）

初始请求行与响应不同。
请求行有三个部分，用空格分隔：

- 方法名（GET、POST、HEAD）
- 请求的资源路径，
- 正在使用的HTTP版本。例如GET / HTTP/1.1

GET是最常见的HTTP方法，用于获取或读取资源，POST是创建资源的常见请求方法，例如使用HTML表单创建新的帖子、上传文件等。

### 初始响应行（状态行）

初始响应行，也称为状态行，也有三个部分，用空格分隔：

- HTTP版本
- 响应状态代码，用于表示请求的结果，以及描述状态代码的原因。状态行的示例包括：
  HTTP/1.0 200 OK
  或
  HTTP/1.0 404 Not Found
  注意：

最常见的状态代码有：
200 OK：请求成功，结果资源（例如文件或脚本输出）在消息正文中返回。
500 服务器错误
可以在此处找到完整的HTTP状态代码列表：[链接](https://httpstatuses.com/)。也可以在此处找到：[链接](https://httpstatusdogs.com/)。

### 头字段

正如您在上面的截图中看到的那样，头行提供了有关请求或响应的信息，或有关消息主体中发送的对象的信息。

```sh
GET / HTTP/1.1
Host: thirtydaysofpython-v1-final.herokuapp.com
Connection: keep-alive
Pragma: no-cache
Cache-Control: no-cache
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/79.0.3945.79 Safari/537.36
Sec-Fetch-User: ?1
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Referer: https://thirtydaysofpython-v1-final.herokuapp.com/post
Accept-Encoding: gzip, deflate, br
Accept-Language: en-GB,en;q=0.9,fi-FI;q=0.8,fi;q=0.

7,en-CA;q=0.6,en-US;q=0.5,fr;q=0.4
```

### 消息主体

HTTP消息可能包含在头行之后发送的数据主体。在响应中，这是返回给客户端的请求资源所在的地方（消息主体的最常见用途），或者如果存在错误的话，可能是解释性文本。在请求中，这是用户输入的数据或上传的文件发送到服务器的地方。

如果HTTP消息包含正文，通常在消息中有描述正文的头行。特别是，

Content-Type：头提供正文中数据的MIME类型（text/html、application/json、text/plain、text/css、image/gif）。
Content-Length：头提供正文中的字节数。

### 请求方法

GET、POST、PUT和DELETE是我们将要实现API或CRUD操作应用程序的HTTP请求方法。

1. GET：GET方法用于使用给定的URI从给定服务器检索和获取信息。使用GET的请求应该只检索数据，对数据没有其他影响。

2. POST：POST请求用于创建数据并将数据发送到服务器，例如，使用HTML表单创建新的帖子、上传文件等。

3. PUT：用上传的内容替换目标资源的所有当前表示，并且我们使用它来修改或更新数据。

4. DELETE：删除数据

