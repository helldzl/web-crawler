FORMAT: 1A
HOST: http://192.168.1.138/

# topics-2.2.0

2.2.0 mifan API 

+ 2017年12月19日
    + Folders API 
        + 增加是否可删除字段
        + 增加关联关系相关API
        + 增加include语义

+ 2017年12月14日
    + Folders API 
        + 增加统计数

## (POST|GET) 目录文件 [/article/folders]

+ Description
    + [MUST] Authticated
    + [MUST] ROLE_USER 角色只能操作用户自己的资源
    + [SHOULD] ROLE_ADMIN 角色不受限制, 会覆盖系统过滤参数 (后台管理功能预留)
        + include=admin
    + 查询列表时需要带上条件, 只查询特定类型的目录
        + filter[folderType]=1
    + 查询列表时, 系统强制过滤参数, 不需要手工指定
        + filter[creator]={current user}
        + filter[enabled]=1
    + [GET] 查询列表时增加以下参数以判断目录下是否包含特定topic ID
        + include={topicId-1[,topicId-2]}

+ Field
    + id (long) - 目录ID
    + folderName (string) - 目录名称
    + folderType (int) - 此处固定为1, 1:产品比较目录类型
    + amount (int) - 当前文件夹文件数
    + capacity (int) - 文件夹总容量
    + cancellable (int) - 1:可删除, 0:不能删除
    + checked (boolean) - true:包含, false:不包含
        + e.g : ?include=1,2,3

+ Meta
    + number (int) - 当前页
    + size (int) - 每页大小
    + numberOfElements (int) - 当前页有多少记录
    + last (boolean) - 是否是最后一页
    + totalPages (int) - 总页数
    + sort (object) - 排序相关信息
    + first (boolean) - 是否是第一页
    + totalElements - 总记录数

### 新增目录 [POST]

+ Request (application/json)

        {
            "data": {
                "folderName": "我的目录",
                "folderType": 1
            }
        }

+ Response 201 (application/json)

    + Headers

            Location: /article/folders/1

    + Body

            {
                "data": {
                    "id": 1,
                    "type": "folder"
                }
            }
            
+ Response 204 (application/json)
        
+ Response 400 (application/json)

        {
            "errors": [
                {
                    "status": "400",
                    "code": "some code",
                    "title": "Bad Request",
                    "detail": "格式错误",
                    "source": {
                        "pointer": "{class} -> {field}"
                    }
                }
            ]
        }

### 查询目录列表 [GET]

+ Response 200 (application/json)

        {
            "meta": {
                "totalPages": 1,
                "totalElements": 3,
                "size": 10,
                "number": 1,
                "numberOfElements": 3,
                "first": true,
                "last": true,
                "sort": null
            },
            "links": {
                "self": "/article/folders?filter[folderType]=1&page[number]=1&page[size]=10",
                "first": "/article/folders?filter[folderType]=1&page[number]=1&page[size]=10",
                "last": "/article/folders?filter[folderType]=1&page[number]=1&page[size]=10"
            },
            "data": [
                {
                    "id": 1,
                    "enabled": 1,
                    "creator": 12,
                    "modifier": 12,
                    "created": "2017-12-13 18:39:12",
                    "modified": "2017-12-13 18:43:23",
                    "parentId": 0,
                    "folderType": 1,
                    "folderName": "吉他相关",
                    "amount": 0,
                    "capacity": 6,
                    "displayOrder": 0,
                    "cancellable": 0,
                    "checked": true
                },
                {
                    "id": 2,
                    "enabled": 1,
                    "creator": 12,
                    "modifier": 12,
                    "created": "2017-12-13 18:40:12",
                    "modified": "2017-12-13 18:44:00",
                    "parentId": 0,
                    "folderType": 1,
                    "folderName": "扩声相关",
                    "amount": 0,
                    "capacity": 6,
                    "displayOrder": 0,
                    "cancellable": 1,
                    "checked": false
                },
                {
                    "id": 3,
                    "enabled": 1,
                    "creator": 12,
                    "modifier": 12,
                    "created": "2017-12-13 18:40:12",
                    "modified": "2017-12-13 18:40:12",
                    "parentId": 0,
                    "folderType": 1,
                    "folderName": "专业相关",
                    "amount": 0,
                    "capacity": 6,
                    "displayOrder": 0,
                    "cancellable": 1,
                    "checked": false
                }
            ]
        }
        
## (GET|DELETE|PATCH)  [/article/folders/{id}]

+ Description
    + 同上

+ Parameters
    + id (long) - 目录ID

### 查询目录详情 [GET]

+ Response 200 (application/json)

        {
            "data": {
                "id": 1,
                "enabled": 1,
                "creator": 12,
                "modifier": 12,
                "created": "2017-12-13 18:39:12",
                "modified": "2017-12-13 18:43:23",
                "parentId": 0,
                "folderType": 1,
                "folderName": "吉他相关",
                "displayOrder": 0
            }
        }

### 删除目录 [DELETE]

+ Response 204 (application/json)

### 修改目录 [PATCH]

+ Request (application/json)

        {
            "data": {
                "folderName": "新的名字"
            }
        }
        
+ Response 200 (application/json)

+ Response 204 (application/json)

## (POST|DELETE)用户与文件关联关系(比较) [/users/{userId}/relationships/folders]

+ Description
    + [MUST] Authenticated
    + [MUST] 用户只能操作自己的资源
    + [OPTIONAL] 不写meta的话:/users/{userId}/relationships/folders/compare
    
+ Meta
    + relationships (string) - compare:表明这是_用户_与_文件_资源多对多关系中的_主题比较关联_
    
+ Data
    + id (long) - 主题资源唯一标识符
    + attributes (object, nullable) - 资源属性
    + attributes.topicId (long) - 一次添加单个
    + attributes.topicIds (array) - 一次添加多个

+ Parameters
    + userId (long) - 用户ID

### 增加关联 [POST]

+ e.g : 下面请求为当前用户
    + 将ID=101的Topics添加到ID=1的Folders中, 且
    + 将ID=201, 202的Topics添加到ID=2的Folders中
    + topicId与topicIds必须选择一个

+ Request (application/json)

        {
            "meta": {
                "relationships": "compare"
            },
            "data": [
                {
                    "id": "1",
                    "attributes": {
                        "topicId": 101
                    }
                },
                {
                    "id": "2",
                    "attributes": {
                        "topicIds": [
                            201,
                            202
                        ]
                    }
                }
            ]
        }

+ Response 200 (application/json)

+ Response 202 (application/json)

+ Response 204 (application/json)

+ Response 400 (application/json)

        {
            "errors": [
                {
                    "status": "400",
                    "code": "应用程序code编码",
                    "title": "Bad Request",
                    "detail": "错误信息描述"
                }
            ]
        }

### 删除关联, 清空目录下的主题 [DELETE]

+ e.g : 下面请求为当前用户
    + 清空ID=1的Folders中的所有主题
    + 清空ID=2的Folders中的所有主题
    + 删除单个主题请参考 /article/usersFoldersCompare/{id} API的[DELETE]方法

+ Request (application/json)

        {
            "meta": {
                "relationships": "compare"
            },
            "data": [
                {
                    "id": "1"
                },
                {
                    "id": "2"
                }
            ]
        }

+ Response 200 (application/json)

+ Response 202 (application/json)

+ Response 204 (application/json)

+ Response 400 (application/json)

        {
            "errors": [
                {
                    "status": "400",
                    "code": "应用程序code编码",
                    "title": "Bad Request",
                    "detail": "错误信息描述"
                }
            ]
        }
        
## (POST|GET) 比较目录下的主题 [/article/usersFoldersCompare]

+ Description
    + [MUST] ROLE_USER 普通用户角色
        + 只能往自己的目录中添加主题
        + 只能往存在的目录中添加主题
        + 只能在topicType = 1的目录中添加主题
    + 查询列表时需要手工指定的过滤条件
        + filter[folderId]={id}
    + 查询列表时的系统强制过滤参数, 不需要手工指定
        + include=topics参数, 查询关联数据的信息
        + filter[userId]={current user}
        + filter[enabled]=1
    + topic对象只有id, title数据有效, 其他数据是基本数据类型的默认值(暂时没有去掉)

+ Field
    + id (long) - ID
    + folderId (long) - 目录ID
    + topicId (long) - 主题ID
    + topic (object) - 主题对象
    + topic.id (long) - 主题ID
    + topic.title (string) - 主题名称

+ Meta
    + number (int) - 当前页
    + size (int) - 每页大小
    + numberOfElements (int) - 当前页有多少记录
    + last (boolean) - 是否是最后一页
    + totalPages (int) - 总页数
    + sort (object) - 排序相关信息
    + first (boolean) - 是否是第一页
    + totalElements - 总记录数

### <del>比较目录下新增主题 [POST]</del>

+ Request (application/json)

        {
            "data": {
                "topicId": "12",
                "folderId": "1"
            }
        }

+ Response 201 (application/json)

    + Headers

            Location: /article/usersFoldersCompare/1

    + Body

            {
                "data": {
                    "id": 1,
                    "type": "usersTopcisCompare"
                }
            }
            
+ Response 204 (application/json)
        
+ Response 400 (application/json)

        {
            "errors": [
                {
                    "status": "400",
                    "code": "some code",
                    "title": "Bad Request",
                    "detail": "格式错误",
                    "source": {
                        "pointer": "{class} -> {field}"
                    }
                }
            ]
        }

### 查询比较目录下的主题列表 [GET]

+ Response 200 (application/json)

        {
            "meta": {
                "totalPages": 1,
                "totalElements": 4,
                "size": 10,
                "number": 1,
                "numberOfElements": 4,
                "first": true,
                "last": true,
                "sort": null
            },
            "links": {
                "self": "/article/usersFoldersCompare?page[number]=1&page[size]=10",
                "first": "/article/usersFoldersCompare?page[number]=1&page[size]=10",
                "last": "/article/usersFoldersCompare?page[number]=1&page[size]=10"
            },
            "data": [
                {
                    "id": 7,
                    "enabled": 1,
                    "created": "2017-12-13 10:32:51",
                    "modified": "2017-12-13 10:32:51",
                    "userId": 12,
                    "topicId": 1,
                    "folderId": 2,
                    "topic": {
                        "id": 1,
                        "title": "Virus TI2 Desktop",
                        "imageSingle": false,
                        "imageRotation": false,
                        "liked": 0,
                        "favorite": 0
                    }
                },
                {
                    "id": 8,
                    "enabled": 1,
                    "created": "2017-12-13 15:26:07",
                    "modified": "2017-12-13 15:30:38",
                    "userId": 12,
                    "topicId": 21,
                    "folderId": 1,
                    "topic": {
                        "id": 21,
                        "title": "Producer 6L 28-watt Handwired Tube Head with 6L6 Tubes",
                        "imageSingle": false,
                        "imageRotation": false,
                        "liked": 0,
                        "favorite": 0
                    }
                },
                {
                    "id": 35,
                    "enabled": 1,
                    "created": "2017-12-14 12:41:03",
                    "modified": "2017-12-14 12:41:03",
                    "userId": 12,
                    "topicId": 12,
                    "folderId": 11,
                    "topic": {
                        "id": 12,
                        "title": "Colour Bender Germanium Handwired Mark II Bender Fuzz Pedal",
                        "imageSingle": false,
                        "imageRotation": false,
                        "liked": 0,
                        "favorite": 0
                    }
                }
            ]
        }
        
## (GET|DELETE|PATCH)  [/article/usersFoldersCompare/{id}]

+ Description
    + PATCH 暂时不支持修改, 通过删除再新增实现
    + GET 语义应该用不到, API从简

+ Parameters
    + id (long) - ID

### <del>查询比较目录下的主题详情 [GET]</del>

+ Response 200 (application/json)

        {
            "data": {
                "id": 38,
                "enabled": 1,
                "created": "2017-12-14 13:42:55",
                "modified": "2017-12-14 13:42:55",
                "userId": 12,
                "topicId": 12,
                "folderId": 1
            }
        }

### 删除比较目录下的主题（1条1条删除） [DELETE]

+ Response 204 (application/json)

### <del>修改比较目录下的主题 [PATCH]</del>

+ Request (application/json)

        {
            "data": {
                "topicId": "12",
                "folderId": "1"
            }
        }
        
+ Response 200 (application/json)

+ Response 204 (application/json)
