---
layout: default
title: 代码规范
---

# 代码规范
{:.no_toc}

* 目录
{:toc}
## 基本代码规范

* 使用 ECMAScript 2018。
* 使用 ECMAScript modules。

### 使用ESLint

代码使用 `ESlint` 作为基本的语法检验工具：

- 以 `eslint:recommended` 作为基础规则
- 不使用分号
- 不使用 `console`
- 不在循环内使用 `await`
- 不存在未使用的变量
- 不存在空代码块
- 省略可省略的括号
- 只是用严格相等

## 前端代码规范


### 基本规范

- 强制使用函数式组件。

- 强制使用 JSX 语法。

### 命名

  - **扩展名**: React 模块使用 `.jsx` 扩展名。

  - **文件名**: 文件名使用帕斯卡命名。如, `ReservationCard.jsx`。

  - **引用命名**: React 模块名使用帕斯卡命名，实例使用骆驼式命名。

  - **模块命名**: 模块使用当前文件名一样的名称。 比如 `ReservationCard.jsx` 应该包含名为 `ReservationCard`的模块。 但是，如果整个文件夹是一个模块，使用 `index.js`作为入口文件，然后直接使用 `index.js` 或者文件夹名作为模块的名称:

  - **高阶模块命名**: 对于生成一个新的模块，其中的模块名 `displayName` 应该为高阶模块名和传入模块名的组合。 例如, 高阶模块 `withFoo()`, 当传入一个 `Bar` 模块的时候， 生成的模块名 `displayName` 应该为 `withFoo(Bar)`。

  - **属性命名**: 避免使用DOM相关的属性来用作其他的用途。

### 声明模块

  - 不要使用 `displayName` 来命名React模块，而是使用引用来命名模块， 如 class 名称。

### 代码对齐

  - 遵循以下的JSX语法缩进/格式。

    ```jsx
    // bad
    <Foo superLongParam="bar"
         anotherSuperLongParam="baz" />

    // good, 有多行属性的话, 新建一行关闭标签
    <Foo
      superLongParam="bar"
      anotherSuperLongParam="baz"
    />

    // 若能在一行中显示, 直接写成一行
    <Foo bar="bar" />

    // 子元素按照常规方式缩进
    <Foo
      superLongParam="bar"
      anotherSuperLongParam="baz"
    >
      <Quux />
    </Foo>
    ```

### 引号

  - 对于JSX属性值总是使用双引号(`"`), 其他均使用单引号(`'`)。 

### 空格

  - 总是在自关闭的标签前加一个空格，正常情况下也不需要换行。

  - 不要在JSX `{}` 引用括号里两边加空格。

### Props

  - JSX属性名使用骆驼式风格`camelCase`。

  - 如果属性值为 `true`, 可以直接省略。

  - `<img>` 标签总是添加 `alt` 属性。 如果图片以presentation(感觉是以类似PPT方式显示?)方式显示，`alt` 可为空, 或者`<img>` 要包含`role="presentation"`。 

  - 不要在 `alt` 值里使用如 "image", "photo", or "picture"包括图片含义这样的词， 中文也一样。 

  - 尽可能少地使用扩展运算符         

### Refs

  - 总是在Refs里使用回调函数。

### 括号

  - 将多行的JSX标签写在 `()`内。

### 标签

  - 对于没有子元素的标签来说总是自己关闭标签。

  - 如果模块有多行的属性，关闭标签时新建一行。

### 函数

  - 使用箭头函数来获取本地变量。

    

