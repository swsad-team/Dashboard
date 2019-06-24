---
layout: default
title: 代码规范
---

# 代码规范
{:.no_toc}

* 目录
{:toc}

## 前端代码规范
> Airbnb React/JSX 编码规范

### 内容目录

  1. [基本规范](#basic-rules-基本规范)
  1. [Class vs React.createClass vs stateless](#创建模块)
  1. [Mixins](#mixins)
  1. [命名](#naming-命名)
  1. [声明模块](#declaration-声明模块)
  1. [代码对齐](#alignment-代码对齐)
  1. [单引号还是双引号](#quotes-单引号还是双引号)
  1. [空格](#spacing-空格)
  1. [属性](#props-属性)
  1. [Refs引用](#refs)
  1. [括号](#parentheses-括号)
  1. [标签](#tags-标签)
  1. [函数/方法](#methods-函数)

### Basic Rules 基本规范

  - 每个文件只写一个模块.
    - 但是多个无状态模块可以放在单个文件中.
  - 推荐使用JSX语法.
  - 不要使用 `React.createElement`，除非从一个非JSX的文件中初始化你的app.

### 创建模块
   Class vs React.createClass vs stateless  

  - 如果你的模块有内部状态或者是`refs`, 推荐使用 `class extends React.Component` 而不是 `React.createClass`.

  - 如果你的模块没有状态或是没有引用`refs`， 推荐使用普通函数（非箭头函数）而不是类:

### Mixins

  - 不要使用 mixins.

  > 为什么? Mixins 会增加隐式的依赖，导致命名冲突，并且会以雪球式增加复杂度。在大多数情况下Mixins可以被更好的方法替代，如：组件化，高阶组件，工具模块等。

### Naming 命名

  - **扩展名**: React模块使用 `.jsx` 扩展名.
  
  - **文件名**: 文件名使用帕斯卡命名. 如, `ReservationCard.jsx`.
  
  - **引用命名**: React模块名使用帕斯卡命名，实例使用骆驼式命名. eslint: [`react/jsx-pascal-case`](https://github.com/yannickcr/eslint-plugin-react/blob/master/docs/rules/jsx-pascal-case.md)

  - **模块命名**: 模块使用当前文件名一样的名称. 比如 `ReservationCard.jsx` 应该包含名为 `ReservationCard`的模块. 但是，如果整个文件夹是一个模块，使用 `index.js`作为入口文件，然后直接使用 `index.js` 或者文件夹名作为模块的名称:

  - **高阶模块命名**: 对于生成一个新的模块，其中的模块名 `displayName` 应该为高阶模块名和传入模块名的组合. 例如, 高阶模块 `withFoo()`, 当传入一个 `Bar` 模块的时候， 生成的模块名 `displayName` 应该为 `withFoo(Bar)`.

    > 为什么？一个模块的 `displayName` 可能会在开发者工具或者错误信息中使用到，因此有一个能清楚的表达这层关系的值能帮助我们更好的理解模块发生了什么，更好的Debug.
  
  - **属性命名**: 避免使用DOM相关的属性来用作其他的用途。

    > 为什么？对于`style` 和 `className`这样的属性名，我们都会默认它们代表一些特殊的含义，如元素的样式，CSS class的名称。在你的应用中使用这些属性来表示其他的含义会使你的代码更难阅读，更难维护，并且可能会引起bug。

### Declaration 声明模块

  - 不要使用 `displayName` 来命名React模块，而是使用引用来命名模块， 如 class 名称.

### Alignment 代码对齐

  - 遵循以下的JSX语法缩进/格式.

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

### Quotes 单引号还是双引号
  
  - 对于JSX属性值总是使用双引号(`"`), 其他均使用单引号(`'`). 

### Spacing 空格

  - 总是在自动关闭的标签前加一个空格，正常情况下也不需要换行.

  - 不要在JSX `{}` 引用括号里两边加空格.

### Props 属性

  - JSX属性名使用骆驼式风格`camelCase`.

  - 如果属性值为 `true`, 可以直接省略.

  - `<img>` 标签总是添加 `alt` 属性. 如果图片以presentation(感觉是以类似PPT方式显示?)方式显示，`alt` 可为空, 或者`<img>` 要包含`role="presentation"`. 
  
  - 不要在 `alt` 值里使用如 "image", "photo", or "picture"包括图片含义这样的词， 中文也一样. 

  - 使用有效正确的 aria `role`属性值 ARIA roles. 

  - 不要在标签上使用 `accessKey` 属性. 

  - 避免使用数组的index来作为属性`key`的值，推荐使用唯一ID. 

  - 对于所有非必须的属性，总是手动去定义`defaultProps`属性.    
  
  - 尽可能少地使用扩展运算符         
  
  例外情况:  
  
  -  使用了变量提升的高阶组件    
  
  -  只有在清楚明白扩展对象时才使用扩展运算符。这非常有用尤其是在使用Mocha测试组件的时候。   
  
  特别提醒：尽可能地筛选出不必要的属性。

### Refs

  - 总是在Refs里使用回调函数.

### Parentheses 括号

  - 将多行的JSX标签写在 `()`里. 

### Tags 标签

  - 对于没有子元素的标签来说总是自己关闭标签. 

  - 如果模块有多行的属性，关闭标签时新建一行. 

### Methods 函数

  - 使用箭头函数来获取本地变量.
 
  - 当在 `render()` 里使用事件处理方法时，提前在构造函数里把 `this` 绑定上去. 
 
  - 在React模块中，不要给所谓的私有函数添加 `_` 前缀，本质上它并不是私有的.

  - 在 `render` 方法中总是确保 `return` 返回值. 

## 后端代码规范

### 使用ESLint

代码使用 `ESlint` 作为基本的语法检验工具：

- `Eslint Config Standard` 作为基础规则
- 使用分号
- 函数参数列表前需要有括号
- 对象花括号中必须有空格
- 箭头函数参数列表按需添加括号
- 不适用console
- 允许非驼峰式命名
- 基于 `JavaScript Standard Style`][10]`

额外规则：

- 永远不省略分号
- 可以使用Async/Await的地方就不使用Promise
- Vue组建名字采用pascal命名法，即首字母大写的驼峰式命名，如LoginBox.vue
- 组件文件和组件使用相同的名字，组件名必须避免使用Vue保留标签名（包括HTML标签和Vue内部标签）
- JS变量名、参数名、函数名：必须使用camel命名法。

命名同时还需要关注语义，如：

- 变量名应当使用名词camel命名
- boolean类型的应当使用is、has等起头,表示其类型
- 函数名应当用动宾短语
