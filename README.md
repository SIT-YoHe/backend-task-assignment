### 项目需求

#### 1. **项目概述**

开发一个简单的 RESTful API，支持对用户资源进行基本的 CRUD 操作（创建、读取、更新、删除），并支持分页列举查询。API 应具备以下功能：

- 获取所有用户（支持分页）
- 获取单个用户
- 创建新用户
- 更新现有用户
- 删除用户

#### 2. **数据模型**

用户资源的数据模型如下：

```json
{
  "uid": 1,
  "name": "Alice",
  "email": "alice@example.com"
}
```

- `uid`：用户唯一标识符 uid（整数，自增）
- `name`：用户姓名（字符串）
- `email`：用户邮箱（字符串）

#### 3. **API 接口**

API 应提供以下接口：

- **GET /users**：获取所有用户（支持分页查询）
- **GET /users/{uid}**：获取单个用户
- **POST /users**：创建新用户
- **PUT /users/{uid}**：更新现有用户
- **DELETE /users/{uid}**：删除用户

#### 4. **请求和响应示例**

##### 获取所有用户（分页查询）

**请求**：

```bash
GET /users?marker=1&limit=10
```

- `marker`：游标，一般用于分页查询的起始位置（可选）
- `limit`：每页记录数（可选，默认值为 10，最小值和默认值相同，最大值为 100, 小于最小值取最小值，超过最大值取最大值）

**响应**：

```bash
200 OK
{
  "users": [
    {
      "uid": 1,
      "name": "Alice",
      "email": "alice@example.com"
    },
    {
      "uid": 2,
      "name": "Bob",
      "email": "bob@example.com"
    },
    ...
  ]
}
```

- `users`：用户列表

##### 获取单个用户

**请求**：

```bash
GET /users/1
```

**响应**：

```bash
200 OK
{
  "uid": 1,
  "name": "Alice",
  "email": "alice@example.com"
}
```

##### 创建新用户

**请求**：

```bash
POST /users
Content-Type: application/json

{
  "name": "Charlie",
  "email": "charlie@example.com"
}
```

**响应**：

```bash
200 OK
{
  "uid": 3
}
```

##### 更新现有用户

**请求**：

```bash
PUT /users/1
Content-Type: application/json

{
  "name": "Alice Smith",
  "email": "alice.smith@example.com"
}
```

**响应**：

```json
200 OK
```

##### 删除用户

**请求**：

```bash
DELETE /users/1
```

**响应**：

```bash
200 OK
```

#### 5. **技术要求**

- 使用 Go 语言编写 API, 可以改进 API 设计，尽量遵循[RESTful API 设计规范](https://restfulapi.cn/archives/44)。
- 使用 `net/http` 标准库或第三方库（如 [gin](https://github.com/gin-gonic/gin), [gorilla/mux](https://github.com/gorilla/mux)）处理 HTTP 请求和路由。
- 使用 JSON 格式进行数据传输。
- 使用内存存储用户数据，使用本地 JSON 文件持久化用户数据。
- 实现基本的错误处理，如用户不存在时的错误响应。（可自行设计错误消息风格）
- 提供 API 文档，说明每个接口的请求和响应格式（建议包含所有可能的错误响应）。
- 需要 fork 本仓库并新开开发分支，通过 PR 的形式提交已完成的代码到本仓库。

#### 6. **可选额外要求**

- 加入接口鉴权支持，可考虑使用[JWT](https://jwt.io/)等方案。
- 使用 Dockerfile 和 docker-compose 进行自动化部署。
- 使用 `go test` 编写单元测试。
- 使用 [swag](https://github.com/swaggo/swag) 项目做 Swagger API 文档的自动化生成以方便调试和前端对接。
- 使用数据库进行持久化存储，建议优先选择 [PostgreSQL](https://www.postgresql.org/) 作为数据库解决方案，因其具备更高的性能和强大的功能。不过对于本项目来说，属于轻量级、简单部署的场景，[SQLite](https://www.sqlite.org/) 也是一个可行的选择。
- 使用 [Redis](https://github.com/redis/redis) 做用户数据的缓存。
- 使用 [zap](https://github.com/uber-go/zap) 日志框架记录程序中的关键日志信息。
- 分离程序的配置结构体，通过配置文件加载服务配置（也可以使用现成的 [viper](https://github.com/spf13/viper) 配置框架来读取配置文件）。
