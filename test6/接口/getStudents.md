# 接口：getStudents  [返回](../README.md)
用例： [学生列表](../用例/学生列表.md)

- 权限：
    学生/访客：都可以看到列表
    老师：只有老师能看到列表和成绩

- 功能：
    返回所有学生的列表。

- API请求地址：
   接口基本地址/v1/api/getStudents

- 请求方式 ：
    GET

- 请求参数说明:
    无

- 返回实例：
``` json
        {
            "status": true,
            "info": null,
            "total": 2,
            "data": [
                {
                    "WEB_SUM": "Y,Y,Y,Y,Y,N",
                    "GITHUB_USERNAME": "icemaplen",
                    "STUDENT_ID": "201510414214",
                    "CLASS": "软件(本)15-2",
                    "NAME": "奈飞",
                    "GRADE1":80,
                    "GRADE2":80,
                    "GRADE3":80,
                },
                {
                    "WEB_SUM": "Y,Y,Y,Y,Y,N",
                    "GITHUB_USERNAME": "icemaplen",
                    "STUDENT_ID": "201510414214",
                    "CLASS": "软件(本)15-2",
                    "NAME": "奈飞",
                    "GRADE1":80,
                    "GRADE2":80,
                    "GRADE3":80,
                }
            ]
        }
```

- 返回参数说明：

  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|
  |status|bool类型，true表示正确的返回，false表示有错误|
  |info|返回结果说明信息|
  |total|返回学生人数|
  |data|所有学生的数组|
  |WEB_SUM|网址是否正确的汇总|
  |GITHUB_USERNAME|GITHUB 用户名|
  |STUDENT_ID|学号|
  |CLASS|班级|
  |NAME|真实姓名|
  |GRADE1-3|第1-3次实验成绩|
