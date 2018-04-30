|学号|班级|姓名|
|:-------:|:-------------: | :----------:|
|201510414214|软件(本)15-2|奈飞|

## 图书管理系统的时序图

## 1. 借书用例
## 1.1. 借书用例PlantUML源码

``` sequence
@startuml

title 借书
actor 借书者
actor 管理员
participant 系统界面
participant 读者信息
participant 借阅信息
participant 图书信息


autonumber
activate 借书者
    activate 管理员
        借书者 -> 管理员 : 借书
	    管理员 -> 系统界面 :  输入借书者账号
        activate 系统界面
            系统界面 -> 读者信息 : 查询读者信息
            activate 读者信息
                读者信息 -> 系统界面 : 返回读者信息
            deactivate 读者信息
            loop
                系统界面 -> 借阅信息 : 创建借书记录
                activate 借阅信息
                    借阅信息 -> 图书信息 : 更新图书信息
                    activate 图书信息
                        图书信息 -> 借阅信息 : 更新成功
                    deactivate 图书信息
                    借阅信息 -> 系统界面 : 借书成功
                deactivate 借阅信息
            end
            系统界面 -> 管理员 : 借书成功
        deactivate 系统界面
        管理员 -> 借书者 : 借书成功
    deactivate 管理员
deactivate 借书者

@enduml
```

## 1.2. 借书用例时序图
![class](https://github.com/icemaplen/is_analysis/blob/master/test4/image/20180430153859.png)

## 1.3. 借书用例时序图说明
参与者有借书者和图书管理员
读者提供所借图书的编号和个人账户，管理员输入读者账号查询读者信息，如果可借创建借书记录和修改图书库存信息。

***

## 2. 还书用例
## 2.1. 还书用例PlantUML源码

``` sequence
@startuml

title 还书
actor 还书者
actor 管理员
participant 系统界面
participant 借阅信息
participant 图书信息


autonumber
activate 还书者
    activate 管理员
        还书者 -> 管理员 : 还书
        loop
            管理员 -> 系统界面 : 输入图书信息
            activate 系统界面
                系统界面 -> 借阅信息 : 删除借书记录
                activate 借阅信息
                    借阅信息 -> 图书信息 : 更新图书信息
                    activate 图书信息
                        图书信息 -> 借阅信息 : 更新成功
                    deactivate 图书信息
                    借阅信息 -> 系统界面 : 还书成功
                deactivate 借阅信息
                系统界面 -> 管理员 : 还书成功
            deactivate 系统界面
        end
        管理员 -> 还书者 : 借书成功
    deactivate 管理员
deactivate 书者

@enduml
```

## 2.2. 还书用例时序图
![class](https://github.com/icemaplen/is_analysis/blob/master/test4/image/20180430154828.png)

## 2.3. 还书用例时序图说明
还书者提供所借图书编号，管理员输入编号还书。
***

## 3. 查询图书
## 3.1. 查询图书用例PlantUML源码

``` sequence
@startuml

title 查询图书
actor 读者
participant 系统界面
participant 图书信息


autonumber
读者 -> 系统界面 : 输入图书名字
activate 读者
    activate 系统界面
        系统界面 -> 图书信息 : 查询
        activate 图书信息
            图书信息 -> 系统界面 : 返回查询信息
        deactivate 图书信息
        系统界面 -> 读者 : 查询成功
    deactivate 系统界面
deactivate 读者

@enduml
```

## 3.2. 查询图书用例时序图
![class](https://github.com/icemaplen/is_analysis/blob/master/test4/image/%E6%88%AA%E5%9B%BE20180430155531.png)

## 3.3. 查询图书用例时序图说明
读者输入图书名字，系统进行查询并返回查询信息。
***