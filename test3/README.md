# 实验3：图书管理系统领域对象建模
|学号|班级|姓名|
|:-------:|:-------------: | :----------:|
|201510414214|软件(本)15-2|奈飞|
## 1. 图书管理系统的类图

### 1.1 类图PlantUML源码如下：

``` class
@startuml
class Reader {
    - id : int
    - name : string
    - sex : char
    - age : int
    - borrowed : Book[]

    + Reader(int id,string name,char sex,int age) : void
    + GetID() : int
    + SetID(int id) : bool
    + SetPassword(string pw) : bool
    + GetName() : string
    + SetName(string name) : bool
    + GetSex() : char
    + SetSex(char sex) : void
    + GetAge() : int 
    + SetAge(int age) : void
    + GetBorrowed() : Borrow[]
    + AddBorrowed(Borrow borrow) : void
    + DeleteBorrowed(Borrow borrow) : void
}

class Book {
    + canBeBorrowed : bool
    - isbn : string
    - title : string
    - author : string
    - type : string
    - press : string

    + Book(int isbn,string title,string author,string type,string press) : void
    + Delete() : void
    + GetISBN() : string
    + GetTitle() : string
    + GetAuthor() : string
    + GetType() : string
    + GetPress() : string
}

class Borrow {
    - readerID : int
    - isbn : string
    - borrowDate : string
    - borrowDuration : string
    - returnData : string

    + Borrow(int readerID,string isbn,string borrowDate,borrowDuration) : void
    + Renew(string borrowDuration) : bool
    + GetReaderID() : int
    + GetISBN() : string
    + GetBorrowData() : string
    + GetBorrowDuration() : string
    + GetReturnData() : string
    + IsOverDue() : bool
}

class Admin {
    - id : int
    - name : string

    + Admin(int id, string name) : void
    + GetID() : int
    + SetName(string name) : bool
    + GetName() : string
    + Borrow(int readerID,string isbn,string borrowDuration) : bool
    + Return(int readerID,string isbn) : void
    + ChangeReaderIDPw(int readerID,string pw) : void
    + AddBook(Book book) : void
    + DeleteBook(Book book) : void
}

Borrow --> Reader
Borrow <-- Book

@enduml
```

### 1.2. 类图如下：

![class](https://github.com/icemaplen/is_analysis/blob/master/test3/iamge/20180417155541.png)

### 1.3. 类图说明：
Reader 类是借阅者的类，包含很多属性，比如id，年龄，名字，性别等。其中主要操作有借书，还书等；
Admin 类是管理员类，有编号和姓名属性，主要操作是书籍的增删，和读者的修改；
Book 类记录了图书的详细内容，包含isbn，书名，出版社等信息；
Borrow 类记录了借书的详细信息，包含借书人id，就、图书isbn，借阅时间，归还时间，是否超期等；

## 2. 图书管理系统的对象图
### 2.1 类Reader的对象图
#### 源码如下：
``` class
@startuml
object Reader{
    id = 13246
    name = "Norvi"
    sex = '男'
    age = 20
}
@enduml
``` 
#### 对象图如下：
![class](https://github.com/icemaplen/is_analysis/blob/master/test3/iamge/20180417160701.png)

### 2.2 类Admin的对象图
#### 源码如下：
``` class
@startuml
object Admin{
    id = 1
    name = "Norvi"
}
@enduml
``` 
#### 对象图如下：
![class](https://github.com/icemaplen/is_analysis/blob/master/test3/iamge/20180417160836.png)

### 2.3 类Book的对象图
#### 源码如下：
``` class
@startuml
object Book{
    isbn = "978-7-115-44131-7"
    title = "C# 6.0 本质论"
    author = "Mark Michaelies"
    type = "IT"
    press = "人民邮电出版社"
}
@enduml
``` 
#### 对象图如下：
![class](https://github.com/icemaplen/is_analysis/blob/master/test3/iamge/20180417161114.png)

### 2.4 类Borrow的对象图
#### 源码如下：
``` class
@startuml
object Borrow{
    ReaderID = 13254
    isbn = "978-7-115-44131-7"
    borrowData = "2018/4/17"
    borrowDuration = "30"
    returnData = "2018/5/16"
}
@enduml
``` 
#### 对象图如下：
![class](https://github.com/icemaplen/is_analysis/blob/master/test3/iamge/20180417161329.png)