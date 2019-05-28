# 数据格式
## User
- User分为**组织号**和**个人号**（两种仅填写信息不同，可执行操作是一样的）

- **通用属性**
  - phone
  - e-mail （用phone或email这两个信息来登录）
  - nickname
  - password
  - isOrganization （是否组织号）
  - icon （头像，用户不选头像则有个默认的）

- **个人号**
  - realname
  - age
  - male / female
  - studentID

- **组织号**
  - name （组织名称，如：中大学生会、皇茶等）
  - address （组织所在地址）

- **其它属性**（不需要用户注册填写的）
  - money
  - ...

## Task
  - **发布人填写**
    - title （如：“关于大学生每日游戏时间”）
    - due time （截止时间）
    - reward （悬赏金额，仅能整数，如2，每个填问卷的人都能获得2金）
    - number of people （需最多多少人填问卷）

  - **无需填写**
    - published time （发布时间）
    - ...

# UI设计
  - 以下设计供参考，由前端的同学决定
    ![](./simple-ui-design.png)
  
  - 先按照上面的数据格式，自定义几个task显示在UI上

  - 点击任务进入问卷页面
