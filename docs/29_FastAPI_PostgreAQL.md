[tiangolo/full-stack-fastapi-postgresql: Full stack, modern web application generator. Using FastAPI, PostgreSQL as database, Docker, automatic HTTPS and more. (github.com)](https://github.com/tiangolo/full-stack-fastapi-postgresql)

## 文字教程

1. **Squash.io 教程**：此教程解释了如何设置 FastAPI 应用程序与 PostgreSQL 的基础知识。它涵盖了创建同步和异步处理程序，配置 SQLAlchemy 进行数据库交互，并提供了常见数据库操作（如检索、插入、更新和删除数据）的代码片段【8†source】。

2. **Codevoweb 教程**：这个资源提供了使用 Python、FastAPI 和 PostgreSQL 构建 CRUD RESTful API 服务器的逐步指南。它包括有关设置环境和数据库的详细说明，并配置了 JWT 用于身份验证【9†source】。

3. **TutLinks 教程**：此教程重点介绍如何在 FastAPI 中实现异步 REST API 与 PostgreSQL。它提供了添加 CORS 到 FastAPI 的见解，管理应用程序启动和关闭事件，并使用 HTTP 动词创建、更新和检索数据。这是一个全面的指南，用于构建具有分页和 CRUD 功能的笔记应用程序【10†source】。



## 视频教程

一些关于如何将 FastAPI 与 PostgreSQL 结合使用的视频教程：

1. **"如何使用 PostgreSQL 构建 FastAPI 应用"**：这个视频提供了一个全面的指南，讲述了如何构建一个集成了 PostgreSQL 的 FastAPI 应用。非常适合想要全面了解整个过程的人。
   - [在 YouTube 上观看](https://www.youtube.com/watch?v=398DuQbQJq0)【16†来源】。

2. **"Fast API 快速课程 | 使用 Postgres、SQL Alchemy、Async 等构建应用程序"**：这是一个速成课程，你可以跟随它来构建一个使用 FastAPI、PostgreSQL、SQL Alchemy 和 Async 的学习管理系统 API。
   - [在 YouTube 上观看](https://www.youtube.com/watch?v=gQTRsZpR7Gw)【17†来源】。

3. **"使用 Fastapi 和 PostgreSQL 创建 RESTful API CRUD"**：这个教程重点介绍了如何创建一个简单的项目来连接 PostgreSQL 和 FastAPI，涵盖了 RESTful API 开发和 CRUD 操作。
   - [在 YouTube 上观看](https://www.youtube.com/watch?v=d_ugoWsvGLI)【18†来源】。

4. **"结合使用 FastAPI、PostgreSQL 和 Docker"**：如果你有兴趣在 FastAPI 和 PostgreSQL 旁边使用 Docker，这个视频是一个很好的资源。它涵盖了使用 FastAPI 和 PostgreSQL 数据库在 Docker 容器中设置基本 API 的过程。
   - [在 YouTube 上观看](https://www.youtube.com/watch?v=2X8B_X2c27Q)【19†来源】。

5. **"使用 FastAPI 和 SQLAlchemy 与 PostgreSQL 数据库"**：本教程介绍了如何使用 FastAPI 连接 PostgreSQL 数据库，并使用 SQLAlchemy 实现基本的 CRUD 功能。
   - [在 YouTube 上观看](https://www.youtube.com/watch?v=Lj7ivxUvSog)【20†来源】。

这些教程应该能为你在构建 FastAPI 和 PostgreSQL 应用程序方面提供坚实的基础和实用的见解。

---

## 需要SQLAlchemy吗

不一定需要使用 SQLAlchemy 来在 FastAPI 中连接到 PostgreSQL 数据库。虽然 SQLAlchemy 是一个非常流行的 ORM（对象关系映射）工具，它可以简化数据库操作并提供额外的抽象层，但它不是必需的。你可以直接使用异步数据库驱动（如 `asyncpg`）来执行 SQL 查询。

如果你选择不使用 ORM（如 SQLAlchemy），你将直接编写原始 SQL 语句来与数据库进行交互。这种方法可以让你拥有更细粒度的控制，尤其是在处理复杂的查询和数据库操作时。然而，它也意味着你需要自己处理一些额外的工作，比如构造查询和解析结果。

以下是一个使用 `asyncpg` 而不是 SQLAlchemy 连接到 PostgreSQL 的示例：

1. **安装依赖项**：
   ```bash
   pip install fastapi uvicorn asyncpg
   ```

2. **设置数据库连接**：
   ```python
   import asyncpg
   from fastapi import FastAPI
   
   app = FastAPI()
   
   @app.on_event("startup")
   async def startup():
       app.state.db = await asyncpg.connect(user='your_username', password='your_password',
                                            database='your_database', host='127.0.0.1')
   
   @app.on_event("shutdown")
   async def shutdown():
       await app.state.db.close()
   ```

3. **在 FastAPI 路径操作中执行 SQL 查询**：
   ```python
   @app.get("/items/")
   async def read_items():
       rows = await app.state.db.fetch("SELECT * FROM items")
       return rows
   ```

4. **运行 FastAPI 应用程序**：
   ```bash
   uvicorn your_fastapi_file:app --reload
   ```

这种方法更接近于底层数据库操作，可能更适合那些对 SQL 很熟悉并且希望直接控制他们数据库交互的用户。不过，如果你的应用程序需要复杂的数据模型或者你希望利用 ORM 提供的便利性和安全性，那么使用 SQLAlchemy 或者其他 ORM 工具可能是更好的选择。