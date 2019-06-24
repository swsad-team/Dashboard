---
layout: default
title: 架构设计、详细设计（BCE方法）到应用程序框架映射指南
---

# 架构设计、详细设计（BCE方法）到应用程序框架映射指南
{:.no_toc}

* 目录
{:toc}

## 逻辑架构

- ![](pics/1.png)

### 表示层

- 用户（任务发布者和接受者）使用Web端作为表示层，提供任务列表的显示与筛选、任务管理系统、任务处理系统、用户管理系统、问卷填写系统。

### 业务层

- 后端服务器充当业务层，根据表示层的请求，完成各个子系统的不同服务模块，向整个系统项目提供不同的功能。

### 持久化层

- MongoDB数据库提供了数据的持久化服务。

## 框架目录

### 前端
```
.
├── public
│   ├── favicon.ico
│   ├── index.html
│   └── manifest.json
├── src
│   ├── apis
│   │   ├── index.js
│   │   ├── instance.js
│   │   └── user.js    
│   ├── components
│   │   ├── AllTaskList.jsx
│   │   ├── AnswerList.jsx
│   │   ├── AppRouter.jsx
│   │   ├── CheckAllBox.jsx
│   │   ├── CreateSurvey.jsx
│   │   ├── FillSurveyPage.jsx
│   │   ├── HomePage.jsx
│   │   ├── LoginForm.jsx
│   │   ├── MyTaskList.jsx
│   │   ├── NewTask.jsx
│   │   ├── RegisterForm.jsx
│   │   ├── SurveyAnswerContainer.jsx
│   │   ├── SurveyWithAnswer.jsx
│   │   ├── TaskBasicForm.jsx
│   │   ├── TaskFilter.jsx
│   │   ├── TaskInfo.jsx
│   │   ├── TaskInfoList.jsx
│   │   ├── TaskList.jsx
│   │   └── TaskListContainer.jsx
│   ├── context
│   │   └── index.js
│   ├── index.css
│   └── index.jsx
├── .travis.yml
├── app.yaml
├── config-overrides.js
├── package-lock.json
├── package.json
└── README.md
```

### 后端
```
.
├── src
│   ├── controller
│   │   ├── task.js
│   │   └── user.js    
│   ├── model
│   │   ├── answerList.js
│   │   ├── global.js
│   │   ├── task.js
│   │   └── user.js
│   ├── router
│   │   ├── baseRouter.js
│   │   ├── taskRouter.js
│   │   └── userRouter.js
│   ├── tests
│   │   └── user.test.js
│   ├── util
│   │   ├── auth.js
│   │   ├── auth.test.js
│   │   └── logger.js
│   ├── app.js
│   ├── config.js
│   └── server.js
├── .eslintrc
├── .prettierrc.json
├── .travis.yaml
├── jest.config.js
├── package.json
└── README.md
```

## ECB

> 逻辑架构对应项目的映射指南

E - Entiry:
  - 系统数据，在本项目中为数据库相应的Model：用户User，任务Task和问卷结果Answer

C - Controller:
  - 对应后端服务器中的controller目录下的内容，接收来自界面的请求之后，对数据进行处理，并且返回数据

B - Boundary:
  - 用户可以交互的Web端界面
  - 服务端的接口
