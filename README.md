# 数据格式

## User
- User分为**组织号**和**个人号**（*斜的数据为用户填写*）

- **通用属性**
  - uid （随机生成）
  - *phone*
  - *e-mail* （用phone或email这两个信息来登录）
  - *name*
  - *password*
  - *isOrganization* （是否组织号）
  - *icon* （头像，用户不选头像则有个默认的）
  - coin （默认100）

- **个人号**
  - *realname*
  - *birthYear*
  - *gender*
  - *studentId*

- **组织号**
  - *address* （组织所在地址）

## Task
  - **task**
    - tid  (randomly get)
    - qid  （questionnaireId, 若为其它任务则none）
    - *title* （如：“关于大学生每日游戏时间”）
    - *description*
    - startTime
    - *endTime*
    - *reward* （悬赏金额）
    - coinPool （奖金池，仅能整数，如20，需10人，则每人获2金）
    - *numOfPeople* （所需人数）
    - participant[] （存储参与者的uid）
    - finisher[]
  
  - **questionnaire**
    - qid
    - question[] （问题1、问题2）
      - isRequired （必填）
      - type （问答、单选、多选）
      - option[] （问答题为none，数组的值为选项内容，如苹果、香蕉）
  
  - **result**
    - aid
    - qid （对应问题的id
    - uid （回答者的id
    - answer[] （例：问答题"happy"，单选"0""1"，多选"012"）

---

# API

1. 