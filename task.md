# 后端学习文档

## 简介

本文档旨在为后端开发初学者提供一个关于Go语言及其相关库的学习路线图。Go语言以其简洁、高效和并发支持而闻名，非常适合构建高性能的后端服务。在本文档中，我们将涵盖Go语言的基础、项目命名规范、开发工具，以及一些流行的Go语言库。

## 要求及计划
 - 10.1前学完golang基础语法并完成IDE环境配置（能在自己电脑上运行go程序）
 - 10.7前独立完成大作业（不过度依赖AI，具体要求见文末）

## 参考资料
阅读以下资料
 - 基础语法 https://www.runoob.com/go/go-tutorial.html 
 - 命名规范 https://cloud.tencent.com/developer/article/2363179 
 - IDE（推荐使用VS Code或Goland） https://www.runoob.com/go/go-ide.html

阅读以下库的文档
 - gin框架 https://github.com/gin-gonic/gin 
 - resty代替http原生库 https://github.com/go-resty/resty 
 - goquery库 https://github.com/PuerkitoBio/goquery
 - Swagger文档 https://github.com/swaggo/gin-swagger 

选读
 - GORM操作数据库 https://github.com/go-gorm/gorm

## 1. Go语言基础

### 1.1 Go语言简介

Go语言是一种开源的编程语言，由Robert Griesemer, Rob Pike, Ken Thompson等人于2007年开发，并在2009年开源。Go语言以其简洁、快速、安全、并行、有趣、开源等特点而受到开发者的喜爱。

- **简洁、快速、安全**：Go语言的设计哲学强调简洁性，提供了快速的编译时间和强大的内存管理。
- **并行、有趣、开源**：Go语言支持并发编程，拥有活跃的社区和丰富的开源资源。

### 1.2 第一个Go程序

要开始Go语言的学习，首先需要编写一个简单的"Hello, World!"程序。以下是一个基本的Go程序示例：

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello, World!")
}
```

使用`go run`命令来运行上述程序。

## 2. Go语言项目命名规范

在Go语言项目开发中，遵循一定的命名规范是非常重要的。这有助于保持代码的一致性和可读性。

### 2.1 包命名规范

- 使用小写字母。
- 避免泛化的名称。

### 2.2 变量和常量命名规范

- 使用驼峰命名法。
- 变量名应该简短且具有描述性。
- 常量名应该全大写，用下划线分隔单词。

### 2.3 函数和方法命名规范

- 使用驼峰命名法。
- 函数名应该使用动词，明确描述函数的操作。

### 2.4 结构体和接口命名规范

- 使用驼峰命名法。
- 避免缩写，除非是广泛接受的行业标准。

### 2.5 测试文件命名规范

- 测试文件应该以`_test.go`结尾。
- 测试函数的命名应以`Test`为前缀。

## 3. 开发工具

### 3.1 VSCode

VSCode是一个流行的代码编辑器，支持Go语言开发。安装Go语言插件后，可以享受代码提示、测试、调试等功能。

### 3.2 GoLand

GoLand是JetBrains开发的Go语言IDE，提供了强大的代码分析、智能补全和调试功能。


## 4. 流行Go语言库

### 4.1 Gin

Gin是一个高性能的Web框架，它提供简洁的API来构建Web应用和API。

- **GitHub地址**：[https://github.com/gin-gonic/gin](https://github.com/gin-gonic/gin)

### 4.2 Resty

Resty是一个简单的Go语言HTTP客户端，用于发送HTTP请求。

- **GitHub地址**：[https://github.com/go-resty/resty](https://github.com/go-resty/resty)

### 4.3 Gin-Swagger

Gin-Swagger为Gin框架提供了Swagger文档生成功能，方便API文档的生成和查看。

- **GitHub地址**：[https://github.com/swaggo/gin-swagger](https://github.com/swaggo/gin-swagger)

### 4.4 GORM(选学)

GORM是一个功能强大的ORM库，用于操作数据库。

- **GitHub地址**：[https://github.com/go-gorm/gorm](https://github.com/go-gorm/gorm)

## 5. 大作业

[https://www.sit.edu.cn/xww/wxgzh.htm](https://www.sit.edu.cn/xww/wxgzh.htm)

 使用goquery库解析上述页面并返回数据，使用gin搭建简单接口，获取实时数据。
 代码大致流程如下：
 1. resty库请求获取上述页面的html
 2. goquery库解析html文档
 3. 根据需求数据自定义结构体
 4. 解析出需要的数据，存入结构体列表
 5. 通过gin返回数据（请求参数可以是页面数）