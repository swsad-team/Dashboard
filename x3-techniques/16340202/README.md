---
layout: default
title: Swagger编写API文档
---

# Swagger编写API文档
{:.no_toc}

* 目录
{:toc}

## 1、简要

### Swagger

  Swagger是一个简单但功能强大的API表达工具，可以产生交互式文档，也有自动生成代码的SDK以及API的发现特性。如今Swagger2.0已经发布，比1.0变得更加强大。

  ![](pics/1.png)

### OpenAPI规范

  V2.0版本的OpenAPI规范，帮助开发者描述一个API的基本信息，如一般性描述、路径、操作等；更简单更快速地表达API。

## 2、使用

  - 一般推荐使用YAML而非JSON格式进行编写，因为其更简单

  - 可以用[在线编辑器](http://editor.swagger.io/)编写

  - 也可以在[本地部署](https://github.com/swagger-api/swagger-codegen)

## 3、编写

### 3.1 版本号
  
  通过一个swagger属性来声明OpenAPI规范版本：
  ```yaml
  swagger: "2.0"
  ```

### 3.2 文档信息

  声明此API文档的相关信息
  ```yaml
  info:
    description: ""
    version: "0.1.0"
    title: "Your API Document Title"
    termsOfService: ""
    contact:
      email: "youremail@developer.com"
    license:
      name: "Apache 2.0"
      url: "http://www.apache.org/licenses/LICENSE-2.0.html"
  ```

### 3.3 URL

  声明API的url，以及其使用的协议
  ```yaml
  schemes:
    - https
    - http
  host: simple.api
  basePath: /v1
  ```

### 3.4 路径

  添加路径，以paths标签，在其下添加'/xxx'这样的形式来添加路由路径，比如以下添加了一个/users，结合上一点，则该路径为: "simple.api/v1/users".

  参数要用 {} 括起来：

  ```yaml
  paths:
    /users:
    /users/{id}:
    /users/{id}/page:
    /tasks:
  ```

### 3.5 标签

  在`paths`的前面，添加一个`tags`，声明本文档会使用的路径分类：
  ```yaml
  tags:
    - name: "user"
      description: "tag of user"
    - name: "task"
      description: "tag of task"
  ```

### 3.6 方法

  在每个路径下，添加任意HTTP动词`GET` `POST` `PUT` `PATCH` `DELETE`等，以添加一个HTTP访问方法。下面的例子即在`/users`添加一个get方法：

  ```yaml
  /users:
    get:
      tags:
        - user
      summary: Get user
      description: Get a user
      parameters:
        # ...
        # see in 3.7
      responses:
        # ...
        # see in 3.8
  ```

  可以用`tags`来标记这个方法，Swagger会将同一tag的API放到一起：

  ![](pics/2.png)

### 3.7 参数

  参数的格式如下：
  ```yaml
  # GET /users/{id}
  parameters:
    - name: id
      in: path
      description: The id of user
      required: true
      type: integer
    - name: secondParam
      #...
  ```

  参数形式有`query` `body` `path` `header` `formData`等

### 3.8 响应

  对每个方法添加**响应**(response)，需要HTTP状态码、描述、以及可能要返回的数据：

  ```yaml
  # GET /users/{id}
  responses:
    200:
      description: return info of a user
      schema:
        $ref: "#/definitions/User"
    400:
      description: user not found
      schema:
        type: string
  ```

  上面的代码可以看到，使用了一个引用`$ref`，这将在3.9介绍。

### 3.9 模型

  在文档尾部添加一个定义项`definitions`，可以定义一些重复使用的数据模型，比如User，然后在API文档中直接引用，这样就不用在每一个方法里都定义一次参数数据格式和响应数据格式了：

  ```yaml
  # models
  definitions:
    User:
      type: object
      properties:
        uid:
          type: number
        name:
          type: string
      xml:
        name: User
    Task:
      type: object
      properties:
        tid:
          type: number
        publisher:
          $ref: "#/definitions/User"
  ```

  以上面的代码为例，我们定义了User和Task的数据格式，User有uid和name两个属性，这样就可以直接用`$ref: "#/definitions/User"`引用了。

### 总结

  以上即为简单使用Swagger编写API文档会用到的基本内容。

## 4、深入

  更多更深入的Swagger使用细则可以去[官网](https://swaggerhub.com/)查看。
