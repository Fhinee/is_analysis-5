# 实验二：图书管理系统用例建模
|学号|班级|姓名|
|:-------:|:-------------: | :----------:|
|201510414214|软件(本)15-2|奈飞|

## 1. 图书管理系统的用例关系图

### 1.1 用例图PlantUML源码如下：

``` uml
@startuml
left to right direction

actor (读者)
actor (图书管理员)
actor (系统管理员)

(系统管理员) --|> (图书管理员)

rectangle 图书管理系统 {
  (读者)-->(登录系统)
  (读者)-->(借书/还书)
  (读者)-->(图书检索)
  (读者)-->(借阅信息查询)
  (读者)-->(查询/修改个人信息)
  (读者)-->(退出系统)

  (图书管理员)-->(登录系统)
  (图书管理员)-->(借书/还书)
  (图书管理员)-->(书籍信息管理)
  (图书管理员)-->(订购书籍)
  (图书管理员)-->(退出系统)
  (图书管理员)-->(图书检索)
  (图书管理员)-->(读者信息管理)

  (系统管理员) --> (系统管理)

  (借书/还书).>(借阅超期罚款):extend
}
@enduml
```


### 1.2. 用例图如下：

![usecase](https://github.com/icemaplen/is_analysis/blob/master/test2/image/20180410170120.png)

## 2. 参与者说明：

###     2.1 图书管理员

主要职责：
- 负责接纳读者借书，还书；
- 以及增添，修改书籍信息；

###     2.2 读者

主要职责是：
- 借阅，归还书籍；
- 查看，修改个人信息；

###     2.3 系统管理员
    
主要职责是：
- 除了拥有图书管理员的权限外还拥有系统权限；
- 负责图书管理员的变更及图书借阅系统的设计，管理，升级与维护；

##     3. 用例规约表

### 3.1 “借出图书”用例

用例名称|借出图书
---|---
参与者|读者，图书管理员
前置条件|正确登录系统，存在目标图书
后置条件|更新借书记录
主事件流|1.登录系统<br>2.查询到目标图书<br>3.确认目标图书有库存，为可借出状态<br>4.更新图书库存数量<br>5.重复2,3,4直到借阅完成


**“借出图书”用例流程图源码如下：**
``` uc1_flow
@startuml
start
:登录系统;
:检索图书;
if(是否存在)then(是)
    if(验证是否可借)then(是)
    while(是否借阅完成)
      :更改图书库存;
      :存储借阅信息;
      :借书成功;
    endwhile
    else(否)
      :借书失败;
      stop
    endif
else(否)
   :借书失败;
   stop
endif
stop
@enduml
```

**“借阅图书”用例流程图源码如下：**

![uc1_flow](https://github.com/icemaplen/is_analysis/blob/master/test2/image/20180410173656.png)

### 3.2 “归还图书”用例

用例名称|归还图书
---|---
参与者|读者，图书管理员
前置条件|图书完好
后置条件|更新借书记录
主事件流|1.输入图书信息<br>2.选择归还<br>3.更新图书库存数量<br>4.重复1,2,3直到归还全部图书
备选事件流|1.书籍损坏或丢失<br>2.赔偿图书


**“归还图书”用例流程图源码如下：**
``` uc2_flow
@startuml
start
while(是否已归还全部图书)
  :输入图书信息;
  if(验证图书是否完好)then(是)
    :更新借书记录;
    :更新图书库存;
  else(否)
    :赔偿图书;
    :更新借书记录;
  endif
endwhile
stop
@enduml
```

**“购入图书”用例流程图源码如下：**

![uc1_flow](https://github.com/icemaplen/is_analysis/blob/master/test2/image/20180410175151.png)