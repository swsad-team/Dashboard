---
layout: default
title: RESTful API 设计规范
---

# RESTful API 设计规范
{:.no_toc}

* 目录
{:toc}

## 1、协议

使用https协议

## 2、路径

REST API是面向资源的，所以路径中只能出现名词，不能出现动词，尽量使用GET,POST来表示动作请求。

## 3、http请求方式

1. GET（SELECT）：从服务器取出资源（一项或多项）。

2. POST（CREATE）：在服务器新建一个资源。

3. PUT（UPDATE）：在服务器更新资源（客户端提供改变后的完整资源）。

4. PATCH（UPDATE）：在服务器更新资源（客户端提供改变的属性）。

5. DELETE（DELETE）：从服务器删除资源。

## 4、过滤与排序

如果对资源的需求不是全部，那么需要提供过滤的参数，同时排序的参数也放在一起，例如：

GET {{url}}/tasks/page=1&per_page=5&sort=time&filter=personal *返回一页5个tasks，按照时间排序，并筛选非个人用户发布的任务*

## 5、数据

使用json数据格式进行数据传递。

## 6、状态码

200 – OK – 一切正常

201 – OK – 新的资源已经成功创建

204 – OK – 资源已经成功擅长

304 – Not Modified – 客户端使用缓存数据

400 – Bad Request – 请求无效，需要附加细节解释如 "JSON无效"

401 – Unauthorized – 请求需要用户验证

403 – Forbidden – 服务器已经理解了请求，但是拒绝服务或这种请求的访问是不允许的。

404 – Not found – 没有发现该资源

422 – Unprocessable Entity – 只有服务器不能处理实体时使用，比如图像不能被格式化，或者重要字段丢失。

500 – Internal Server Error – API开发者应该避免这种错误。