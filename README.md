# api--
仅供学习参考，欢迎交流  914456697



#### 闪帮app接口API相关说明：

* **1.请求的URL：服务器/接口的请求URL 请求登录示例：xxx.xxx.xxx.xxx/flashhelp/user/authorization**
* **2.status   0->成功响应  1->普通错误  2->参数错误  10->用户未登录**
* **3.msg: 当返回错误代码的时候（1 2 10）出现的错误信息**
* **4.data： 当返回成功代码（1）出现的成功的信息或者是数据**
* **5.当响应是错误的时候，需要获取msg的信息 反馈给用户具体的错误信息**
* **6.当响应是成功的时候，极有可能也会带着msg返回给用户以及data数据**
* **7.头像暂时是只能是系统随机提供的头像  大小是400x400**
* **8.所有非GET的请求 数据类型都为JSON  如有特殊情况 接口会注明**


------

#### 1. 用户登录 

*  请求URL
> api/user/authorization
* 请求方式
> POST
* 请求参数

	| 参数| 参数类型| 参数说明  |
	| ---|--------| -- |
	| userName | String |  登录账号，手机号或者账号   |
	| password |   String  | -  |
	| type   |  int | 账号类型，0：账号 1：手机号 2:邮箱 |

* 响应结果

<font color = '#008000' >成功</font>

```
{
    "status": 0,
    "data": {
        "userId": 1,
        "username": "flashhelp",
        "phone": "15555555555",
        "email": "1234@flashhelp.com",
        "autograph": "感谢大家使用闪帮app",
        "registerTime": 1565079301000,
        "isRealname": 0,
        "credit": 100,
        "balance": 0.0,
        "integral": 0,
        "sendList": "0",
        "accept": "0",
        "collection": "0",
        "finish": "0",
        "offtenTask": "10,2,3,4",
        "nikeName": "0",
        "headPhoto": "https://flahhelp.oss-cn-shanghai.aliyuncs.com/img/photo/12.jpeg",
        "sex": 0,
        "location": "0",
        "updateTime": 1566036933000,
        "lastOnLineTime": 1566039628000,
        "activeness": 0,
        "activeness_update_time": null,
        "order_value": 0.0,
        "status": 1
    }
}
```

<font color = '#DC143C' >失败</font>
```
{
    "status": 1,
    "msg": "账号或密码错误"
}
```

------






#### 2.退出登录

*  请求URL
> api/user/authorization
* 请求方式
> DELETE
* 请求参数

	| 参数| 参数类型| 参数说明  |
	| ---|--------| -- |
	| -  |  - | -  |

* 响应结果

<font color = '#008000' >成功</font>

```
{
    "status": 0,
    "data": "退出成功"
}
```

<font color = '#DC143C' >失败</font>
```
{
    "status": 10,
    "msg": "用户未登录，请重新登录后退出"
}
```


#### 3.用户注册

*  请求URL
> api/user
* 请求方式
> POST
* 请求参数

	| 参数| 参数类型| 参数说明  |
	| ---|--------| -- |
	| userName  |  String | 账号   |
    | password   |  String | 密码  |

* 响应结果

<font color = '#008000' >成功</font>

```
{
    "status": 0,
    "data": "注册成功"
}
```
<font color = '#DC143C' >失败</font>
```
{
    "status": 1,
    "msg": "注册失败"
}
```

#### 4.修改资料

*  请求URL
> api/user
* 请求方式
> PUT
* 请求参数
* 建议前端如果用户没有修改任何一项资料就不开放提交按钮

	| 参数| 参数类型| 参数说明  |
	| ---|--------| -- |
	| phone  |  String | 手机号码 可为null |
	| email  |  String | 电子邮箱 可为null |
	| nikeName  |  String | 用户昵称 可为null |
	| headPhoto  |  String | 用户头像 可为null  头像暂时不能修改，可以上传参数但是无法显示正确的头像 |
	| sex  |  String | 性别 可为null |
	| location  |  String | 位置 可为null |
	| autograph  |  String | 签名 可为null |


* 响应结果

<font color = '#008000' >成功</font>

```
{
    "status": 0,
    "data": "修改资料成功"
}
```
<font color = '#DC143C' >失败</font>
```
{
    "status": 1,
    "msg": "修改资料失败，手机号/邮箱 已经被注册"
}

{
    "status": 10,
    "msg": "需要登陆"
}
```

#### 5.修改密码

*  请求URL
> api/user/psw
* 请求方式
> PUT
* 请求参数

	| 参数| 参数类型| 参数说明  |
	| ---|--------| -- |
	| password |  String | 用户修改的新密码  |

* 响应结果

<font color = '#008000' >成功</font>

```
{
    "status": 0,
    "data": "密码修改成功"
}
```

<font color = '#DC143C' >失败</font>
```
{
    "status": 10,
    "msg": "需要登陆"
}
```

#### 6.检查用户名是否已经存在

*  请求URL
> api/user/username/{username}
* 请求方式
> GET
* 请求参数

	| 参数| 参数类型| 参数说明  |
	| ---|--------| -- |
	
* 响应结果

<font color = '#008000' >成功</font>

```
{
    "status": 0
}
```

<font color = '#DC143C' >失败</font>
```
{
    "status": 1,
    "msg": "用户名已被注册"
}
```

#### 7.检查手机号是否已经存在

*  请求URL
> api/user/phone/{phoneNumber}
* 请求方式
> GET
* 请求参数

	| 参数| 参数类型| 参数说明  |
	| ---|--------| -- |

* 响应结果

<font color = '#008000' >成功</font>

```
{
    "status": 0
}
```

<font color = '#DC143C' >失败</font>
```
{
    "status": 1,
    "msg": "手机号已被注册,您可以选择登录"
}
```

#### 8.检查邮箱是否已经存在

*  请求URL
> api/user/email
* 请求方式
> GET
* 请求参数

	| 参数| 参数类型| 参数说明  |
	| ---|--------| -- |
	| email  |  String | 邮箱  |

* 响应结果

<font color = '#008000' >成功</font>

```
{
    "status": 0
}
```

<font color = '#DC143C' >失败</font>
```
{
    "status": 1,
    "msg": "邮箱已经被注册"
}

```



#### 9.获取在线的用户列表

*  请求URL
> api/user
* 请求方式
> GET
* 请求参数

	| 参数| 参数类型| 参数说明  |
	| ---|--------| -- |
	| pageNum  |  Integer | 分页参数，当前页 1-n  |
	| pageSize  |  Integer | 每一页显示的大小   |
	| which_time  |  Integer | 按时间筛选  1：今天 7：一周内  30：一个月内 不填：按数据库顺序列出|
	| order_type  |  String | 排序方式  fans :按人气排序  activeness:活跃度   distance:距离最近的  不填：默认为综合排序  |
	| task_tag  |  Integer | 按任务标签分类，不填：默认不筛选标签  |

* 响应结果

<font color = '#008000' >成功</font>

```
{
    "status": 0,
    "data": {
        "pageNum": 0,
        "pageSize": 0,
        "size": 0,
        "orderBy": null,
        "startRow": 0,
        "endRow": 0,
        "total": 0,
        "pages": 0,
        "list": [
            {
                "userId": 1,
                "username": "flashhelp",
                "phone": "15555555555",
                "email": "1234@flashhelp.com",
                "autograph": "感谢大家使用闪帮app",
                "registerTime": 1565079301000,
                "isRealname": 0,
                "credit": 100,
                "balance": 0.0,
                "integral": 0,
                "sendList": "0",
                "accept": "0",
                "collection": "0",
                "finish": "0",
                "offtenTask": "10,2,3,4",
                "nikeName": "0",
                "headPhoto": "https://flahhelp.oss-cn-shanghai.aliyuncs.com/img/photo/12.jpeg",
                "sex": 0,
                "location": "0",
                "updateTime": 1566036933000,
                "lastOnLineTime": 1566039628000,
                "activeness": 0,
                "activeness_update_time": null,
                "order_value": 0.0,
                "status": 1
            }
        ],
        "firstPage": 0,
        "prePage": 0,
        "nextPage": 0,
        "lastPage": 0,
        "isFirstPage": false,
        "isLastPage": false,
        "hasPreviousPage": false,
        "hasNextPage": false,
        "navigatePages": 0,
        "navigatepageNums": null
    }
}
```

<font color = '#DC143C' >失败</font>
```
{
    "status": 10,
    "msg": "需要登陆"
}

```





#### 10.获取某个用户的详细信息

*  请求URL
> api/user/{userId}
* 请求方式
> GET
* 请求参数

	| 参数| 参数类型| 参数说明  |
	| ---|--------| -- |
	| -  |  - | -  |

* 响应结果

<font color = '#008000' >成功</font>

```
{
    "status": 0,
    "data": {
        "userId": 1,
        "userName": "flashhelp",
        "isRealname": 0,
        "autograph": "感谢大家使用闪帮app",
        "headPhoto": "https://flahhelp.oss-cn-shanghai.aliyuncs.com/img/photo/12.jpeg",
        "credit": 100,
        "offtenTask": "10,2,3,4",
        "fans": 1,
        "taskCommentVoList": []
    }
}
```

<font color = '#DC143C' >失败</font>
```
{
    "status": 1,
    "msg": "用户不存在"
}
```




#### 11.修改头像

*  请求URL
> /api/user/photo
* 请求方式
> POST
* 请求参数

	| 参数| 参数类型| 参数说明  |
	| ---|--------| -- |
	| file  |  file | 表单记得加上 enctype="multipart/form-data" |

* 响应结果

<font color = '#008000' >成功</font>

```
{
	"status": 0,
	"data": "img/user_image/flashhelp/8a5af2c4-c088-4eb4-beba-9d3d5885ad32.jpeg"
}
```

<font color = '#DC143C' >失败</font>
```
{
    "status": 1,
    "msg": "上传头像失败"
}
```












#### 0.模板

*  请求URL
> /xx/xxx
* 请求方式
> POST
* 请求参数

	| 参数| 参数类型| 参数说明  |
	| ---|--------| -- |
	| -  |  - | -  |

* 响应结果

<font color = '#008000' >成功</font>

```
{
    "status": 0,
    data:xxx
}
```

<font color = '#DC143C' >失败</font>
```
{
    "status": 1,
    "msg": "xxxxx"
}
```
------
