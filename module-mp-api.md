# 美频

美频 API 

+ 2018年3月30日
    + 初始化
+ 2018年3月31日
    + 后台品牌管理api
+ 2018年4月11日
    + 后台分类管理api

+ Data
    + mpBrands - 美频品牌
        + id (long) - 标识
        + title (String) - 品牌名
        + description (String) - 品牌介绍/描述
        + feature (String) - 属性
            + location (String) - 公司总部
            + history (String) - 品牌历史
        + image (String) - 图片
        + enabled (int) - 是否可用 0/1:否/是
        + creator (long)
        + modifier (long)
        + created (date)
        + modified (date)
    + mpCategoires - 美频产品教程分类
        + id (long)
        + rootId (long) - 根标识
        + parentId (long) - 父标识
        + type (int) - 0:大类,1:型号,2:小类
        + title (String) - 标题
        + image (String) - 图片
        + mobileImage (String) - 手机版图片
        + path (String) - 路径
        + depth (String) - 深度
        + leaf (int) - 是否叶子节点 0/1:否/是
        + displayOrder (int) - 排序
        + enabled (int) - 是否可用 0/1:否/是
        + creator (long)
        + modifier (long)
        + created (date)
        + modified (date)
    + MpDownloadCategories - 美频下载分类
        + id (long)
        + displayOrder (int) - 排序
        + categoryTitle (String) - 标题
        + image (String) - 图片
        + enabled (int) - 是否可用 0/1:否/是
        + creator (long)
        + modifier (long)
        + created (date)
        + modified (date)
    + mpDownloads - 美频下载
        + id (long)
        + categoryId (long) - 分类标识
        + displayOrder (int) - 排序
        + title (String) - 标题
        + description (String) - 描述
        + image (String) - 图片
        + link (String) - 下载链接
        + times (int) - 下载次数
        + enabled (int) - 是否可用 0/1:否/是
        + creator (long)
        + modifier (long)
        + created (date)
        + modified (date)
    + topics 美频文章
        + title (String) - 产品标题
        + forumId (long) - 模块标识，7：美频技术支持8：美频行业新闻
        + description (String) - 描述
        + id (long) - 新闻标识
        + content (String) - 内容，富文本编辑框
        + tags (long[]) - 标签
        + images (Object[]) - 图片
        + creator (long) - 创建人
        + modifier (long) - 修改人
        + categoryId (long) - 3978：常见问题，3979：知识库，3980：产品教程
        + topicsMp - 美频文章相关数据
            + id (long)
            + type (int) - 类型：0：图文，1：视频
            + topicId (long) - 主题标识
            + upTimes (int) - 置顶次数
            + mpCategoryId (long) - 美频教程分类标识

# 前台

## 新闻模块

### 首页热门 (GET)/mp/topics/hotnews
+ params
    + filter[forum] 必填6,8
    + page[size] 根据需求填写

### 新闻页 
+ 娱乐轮播图 (GET)/mp/topics/hotnews
    + params
        + filter[forum] 必填6
        + page[size] 根据需求填写
        + fromDays 必填7
+ 行业新闻轮播图 /mp/topics/hotnews
    + params
        + filter[forum] 必填8
        + page[size] 根据需求填写
        + fromDays 必填30
+ 轮播图下方数据 (GET)/topics/search?filter[forum]=6,8&page[number]=1&page[size]=10&agg[size]=-1&sort=-created
    + params
        + filter[forum] 必填6,8
        + agg[size] 必填-1
        + sort 必填-created
        + page[number]
        + page[size]
+ 推荐娱乐新闻 (GET)/mp/topics/anchorRecommends
    + Description  
        + page[size]不能小于filter[seedIds]的个数
+ 推荐行业新闻 (GET)/topics/search?filter[forum]=8&fiter[items.upTimes:gt]=0&agg[size]=-1&sort=-items.upTimes


## 技术支持模块

### 首页
+ 常见问题 | 知识库 (GET)/mp/topics/supports?fromDays=30&filter[forum]=7&filter[categoryId]=xx&page[size]=15
    + params
        + fromDays 从何时开始的点击量排序，根据现在的需求填30就可以
        + filter[forum] 必填7
        + filter[categoryId] 常见问题=3978 | 知识库=3979 待定（这个要注意，测试服务器和生产服务器可能不一样）
        + page[size] 根据需求填写
+ 选择品牌 (GET)/mpBrands
+ 根据品牌查询一级分类及二级分类（产品型号） (GET)/mpCategories/cascade?filter[brandId]=1

### 技术支持页
+ 常见问题 | 知识库轮播图 (接口同首页常见问题|知识库)
+ 轮播图下方数据 (GET)/topics/search?filter[forum]=7&filter[categoryId]=xx&page[number]=1&page[size]=10&agg[size]=-1&sort=-created
    + params
        + filter[forum] 必填7
        + filter[categoryId] 常见问题=3978 | 知识库=3979待定（这个要注意，测试服务器和生产服务器可能不一样）
        + agg[size] 必填-1
        + sort 必填-created
        + page[number]
        + page[size]
+ 产品教程 (GET)/mpCategories?filter[type]=1&page[number]=1&page[size]=16

### 单个产品教程页
+ 叶子分类查询 (GET)/mpCategories?filter[parentId]=xx&&page[number]=1&page[size]=16
+ 根据叶子节点查询文章列表 (GET)/topics/search?filter[forum]=7&filter[items.mpCategoryId]=xx&page[number]=1&page[size]=10&agg[size]=-1

### 搜索结果页 
    /topics/search?filter[forum]=7&filter[q]=搜索关键字&page[Number]=1&page[size]=10&agg[size]=-1

## 快速下载

### 三个类别一起查出来 （适用于首页|技术支持页|搜索结果页|快速下载页·全部下载） (GET)/mpDownloads/fast?assistantsSize=10&driveSize=10&softwareSize=10
+ params
    + assistantsSize 91助手个数
    + driveSize 驱动个数
    + softwareSize 常用软件个数

### 根据条件筛选（适用于快速下载页·热门下载|最新下载） (GET) /mpDownloads?filter[type]=1&page[size]=15&sort=-times
+ params 
    + filter[type] 0:91助手下载，1：驱动下载，2：常用软件下载
    + times 下载次数
    + created 创建时间

# 后台
## 品牌管理 [/mpBrands]

### 列表 [GET] /mpBrands

+ Parameters
    + filter[id]
    + filter[title]
        + 模糊查询示例：filter[title:like]=%25ic%25 （'%25'为'%'的转义）

+ Response 200 (application/json)

        {
          "meta": {
            "totalPages": 1,
            "totalElements": 7,
            "size": 10,
            "number": 1,
            "numberOfElements": 7,
            "first": true,
            "last": true,
            "sort": null
          },
          "links": {
            "self": "/mpBrands?page[number]=1&page[size]=10",
            "first": "/mpBrands?page[number]=1&page[size]=10",
            "last": "/mpBrands?page[number]=1&page[size]=10"
          },
          "data": [
            {
              "id": 1,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "title": "ICON"
            },
            {
              "id": 2,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "title": "BLUE"
            }
          ]
        }
### 添加品牌 [POST] /mpBrands
+ Description
    + [MUST] Authenticated
    + [MUST] ROLE_ADMIN | MP_ROLE_ADMIN
+ Parameters
    + title - 必填
    + description
    + features
    + image
    + mpCategoryIds

+ 新增Request (application/json)

        {
            "data":{
                "title":"世界著名品牌",
                "description":"我是描绘苏",
                "image":"tupian.jpg",
                "features":[
                            {
                                "_name":"location",
                                "_value":"中国"
                            },{
                                "_name":"website",
                                "_value":"www.baidu.com"
                            },{
                                "_name":"history",
                                "_value":"百度最牛逼"
                            }
                        ],
                "mpCategoryIds":[
                        1000,
                        2000,
                        1000
                    ]
            }
        }
+ Response 201 (application/json)

        {
          "data": {
            "id": 8,
            "type": "mpBrands"
          }
        }
### 修改品牌 [PATCH] /mpBrands/{id}
+ Description
    + [MUST] Authenticated
    + [MUST] ROLE_ADMIN | MP_ROLE_ADMIN
+ Parameters
    + title - 必填
    + description
    + features
    + image
    + mpCategoryIds
+ 修改Request 200 (application/json)
    
        {
            "data":{
                "title":"中国著名品牌",
                "description":"我是描绘苏",
                "images":"zhongguo.jpg",
                "features":[
                            {
                                "_name":"location",
                                "_value":"中国"
                            },{
                                "_name":"website",
                                "_value":"www.baidu.com"
                            },{
                                "_name":"history",
                                "_value":"百度最牛逼"
                            }
                        ],
                "mpCategoryIds":[
                        2,
                        3
                    ]
            }
        }

### 删除品牌 [DELETE] /mpBrands/{id}
+ Description
    + [MUST] Authenticated
    + [MUST] ROLE_ADMIN | MP_ROLE_ADMIN
+ Response 204

### 品牌详情 [GET] /mpBrands/{id}
+ Response 200

        {
          "data": {
            "id": 9,
            "enabled": 1,
            "creator": 1031,
            "modifier": 1031,
            "created": "2018-04-09 17:36:18",
            "modified": "2018-04-10 11:54:23",
            "title": "中国著名品牌",
            "description": "我是描绘苏",
            "features": [
              {
                "_name": "location",
                "_value": "中国"
              },
              {
                "_name": "website",
                "_value": "www.baidu.com"
              },
              {
                "_name": "history",
                "_value": "百度最牛逼"
              }
            ],
            "mpCategories": [
              {
                "id": 2,
                "type": 0,
                "title": "麦克风",
                "leaf": 0
              },
              {
                "id": 3,
                "type": 0,
                "title": "话放/耳放",
                "leaf": 0
              }
            ]
          }
        }

## 分类管理 [/mpCategories]

### 列表 [GET] /mpCategories

+ Parameters
    + filter[id]
    + filter[title]
        + 模糊查询示例：filter[title:like]=%25声卡%25 （'%25'为'%'的转义）
    + page[number]
    + page[size]

+ Response 200 (application/json)
    
        {
          "meta": {
            "totalPages": 67,
            "totalElements": 667,
            "size": 10,
            "number": 1,
            "numberOfElements": 10,
            "first": true,
            "last": false,
            "sort": null
          },
          "links": {
            "self": "/mpCategories?page[number]=1&page[size]=10",
            "first": "/mpCategories?page[number]=1&page[size]=10",
            "next": "/mpCategories?page[number]=2&page[size]=10",
            "last": "/mpCategories?page[number]=67&page[size]=10"
          },
          "data": [
            {
              "id": 1,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "rootId": 1,
              "parentId": 0,
              "type": 0,
              "title": "声卡",
              "path": "1",
              "depth": 1,
              "leaf": 0,
              "displayOrder": 0
            },
            {
              "id": 2,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "rootId": 2,
              "parentId": 0,
              "type": 0,
              "title": "麦克风",
              "path": "2",
              "depth": 1,
              "leaf": 0,
              "displayOrder": 0
            }
          ]
        }

### 型号列表 [GET] /mpCategories/models?filter[parentId]=2

+ Parameters
    + filter[parentId]
    + filter[id]
    + filter[title]
        + 模糊查询示例：filter[title:like]=%25micu%25 （'%25'为'%'的转义）
    + filter[brandId]
    + page[number]
    + page[size]

+ Response 200 (application/json)
    
        {
          "meta": {
            "totalPages": 1,
            "totalElements": 1,
            "size": 10,
            "number": 1,
            "numberOfElements": 1,
            "first": true,
            "last": true,
            "sort": null
          },
          "links": {
            "self": "/mpCategories/models?filter[parentId]=1&filter[id]=7&page[number]=1&page[size]=10",
            "first": "/mpCategories/models?filter[parentId]=1&filter[id]=7&page[number]=1&page[size]=10",
            "last": "/mpCategories/models?filter[parentId]=1&filter[id]=7&page[number]=1&page[size]=10"
          },
          "data": [
            {
              "id": 7,
              "creator": 0,
              "modifier": 0,
              "created": "2018-03-30 11:12:53",
              "modified": "2018-03-30 11:12:53",
              "parentId": 1,
              "type": 1,
              "title": "MICUVST",
              "brandId": 1,
              "brandName": "ICON"
            }
          ]
        }

### 分类详情 [GET] /mpCategories/{id}
+ Response 200

        {
          "data": {
            "id": 665,
            "enabled": 1,
            "creator": 0,
            "modifier": 1031,
            "created": "2018-04-11 11:29:07",
            "modified": "2018-04-11 16:17:38",
            "rootId": 663,
            "parentId": 663,
            "type": 1,
            "title": "下属型222号",
            "path": "663.665",
            "depth": 2,
            "leaf": 0,
            "displayOrder": 0,
            "children": [
              {
                "id": 666,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2018-04-11 11:29:07",
                "modified": "2018-04-11 11:29:07",
                "rootId": 663,
                "parentId": 665,
                "type": 2,
                "title": "硬件/驱动/机架/系统",
                "path": "663.665.666",
                "depth": 3,
                "leaf": 1,
                "displayOrder": 0
              },
              {
                "id": 667,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2018-04-11 11:29:07",
                "modified": "2018-04-11 11:29:07",
                "rootId": 663,
                "parentId": 665,
                "type": 2,
                "title": "直播软件教程",
                "path": "663.665.667",
                "depth": 3,
                "leaf": 1,
                "displayOrder": 0
              },
              {
                "id": 668,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2018-04-11 11:29:07",
                "modified": "2018-04-11 11:29:07",
                "rootId": 663,
                "parentId": 665,
                "type": 2,
                "title": "其他",
                "path": "663.665.668",
                "depth": 3,
                "leaf": 1,
                "displayOrder": 0
              }
            ],
            "brandId": 9,
            "brandName": "中国著名品牌"
          }
        }
        
### 添加分类 [POST] /mpCategories
+ Description
    + [MUST] Authenticated
    + [MUST] ROLE_ADMIN | MP_ROLE_ADMIN
+ Parameters
    + title - 必填
    + type - 必填 0/1:大类/型号
    + parentId 当type=1时必填
    + brandId 当type=1时必填，当type=0时填了没用
    + image
    + mobileImage
    + displayOrder

+ 新增Request (application/json)
    + 添加大类

            {
                "data":{
                    "title":"管理分类测试",
                    "type":0
                }
            }
    + 添加型号
    
            {
                "data":{
                    "title":"型号1",
                    "type":1,
                    "brandId":8,
                    "parentId":663
                }
            }
+ Response 201 (application/json)

        {
          "data": {
            "id": 663,
            "type": "mpCategories"
          }
        }
### 修改分类 [PATCH] /mpCategories/{id}
+ Description
    + [MUST] Authenticated
    + [MUST] ROLE_ADMIN | MP_ROLE_ADMIN
+ Parameters
    + title - 必填
    + brandId 当type=0时填了没用
    + image
    + mobileImage
    + displayOrder
+ 修改Request 200 (application/json)
    
        {
            "data":{
                "title":"型222号",
                "image":"tupian.jpg",
                "brandId":9
            }
        }

### 删除分类 [DELETE] /mpCategories/{id}
+ Description
    + [MUST] Authenticated
    + [MUST] ROLE_ADMIN | MP_ROLE_ADMIN
+ Response 204

## 文章管理 - 行业新闻 | 常见问题 | 知识库 | 产品教程

### (GET)文章集合 [/mp/topics?filter[forumId]=7&filter[categoryId]=3980&page[number]=1&page[size]=15

+ Parameters
    + filter[forumId] 必填 7：技术支持 8：行业新闻
    + filter[categoryId] 3978：常见问题，3979：知识库，3980：产品教程
    + filter[id] - 筛选条件，唯一标识
    + filter[title] - 筛选条件，文章标题
        + 模糊查询示例：filter[title:like]=%25麦克风%25 （'%25'为'%'的转义）

+ Description
    + [MUST] Authenticated
    + [MUST] ROLE_ADMIN | MP_ROLE_ADMIN

+ Response 200 (application/json)

        {
          "meta": {
            "totalPages": 10,
            "totalElements": 20,
            "size": 2,
            "number": 1,
            "numberOfElements": 2,
            "first": true,
            "last": false,
            "sort": [
              {
                "direction": "DESC",
                "property": "modified",
                "ignoreCase": false,
                "nullHandling": "NATIVE",
                "descending": true,
                "ascending": false
              }
            ]
          },
          "links": {
            "self": "/mp/topics?filter=&filter[forumId]=7&filter[categoryId]=3979&fields[topics]=id,title,categoryId,creator,created,modified,modifier&sort=-modified&page[number]=1&page[size]=2",
            "first": "/mp/topics?filter=&filter[forumId]=7&filter[categoryId]=3979&fields[topics]=id,title,categoryId,creator,created,modified,modifier&sort=-modified&page[number]=1&page[size]=2",
            "next": "/mp/topics?filter=&filter[forumId]=7&filter[categoryId]=3979&fields[topics]=id,title,categoryId,creator,created,modified,modifier&sort=-modified&page[number]=2&page[size]=2",
            "last": "/mp/topics?filter=&filter[forumId]=7&filter[categoryId]=3979&fields[topics]=id,title,categoryId,creator,created,modified,modifier&sort=-modified&page[number]=10&page[size]=2"
          },
          "data": [
            {
              "id": 995409,
              "creator": 0,
              "modifier": 0,
              "created": "2018-01-17 20:07:00",
              "modified": "2018-04-04 14:02:05",
              "categoryId": 3979,
              "title": "EQ均衡器调节方法",
              "imageSingle": false,
              "imageRotation": false,
              "liked": 0,
              "favorite": 0
            },
            {
              "id": 995476,
              "creator": 0,
              "modifier": 0,
              "created": "2018-01-17 20:07:23",
              "modified": "2018-04-04 14:02:04",
              "categoryId": 3979,
              "title": "音频码率",
              "imageSingle": false,
              "imageRotation": false,
              "liked": 0,
              "favorite": 0
            }
          ]
        }
### (GET)文章详情 [/mp/topics/{id}]

+ Description
    + [MUST] Authenticated
    + [MUST] ROLE_ADMIN | MP_ROLE_ADMIN
+ Response 200 (application/json)

        {
          "data": {
            "id": 995249,
            "creator": 0,
            "modifier": 0,
            "created": "2018-03-14 13:20:55",
            "modified": "2018-04-04 14:02:20",
            "forumId": 7,
            "categoryId": 3980,
            "title": "6NANO 硬件安装",
            "topicType": 0,
            "reviews": 0,
            "replies": 0,
            "thumbsUp": 0,
            "thumbsDown": 0,
            "boost": 1,
            "trainSample": 0,
            "locked": 0,
            "moderated": 0,
            "categoryPath": "3980",
            "similarities": [],
            "rotations": [],
            "images": [],
            "audios": [],
            "videos": [],
            "coverImages": [],
            "from": {
              "id": 975314,
              "topicId": 995249,
              "seedId": 123,
              "origin": "http://www.91yp.cn/index.php?m=content&c=index&a=show&catid=49&id=35",
              "rating": 0,
              "reviews": 0,
              "thumbsUp": 0,
              "host": "http://www.91yp.cn",
              "source": "美频",
              "image": "http://static.budee.com/yyren/image/channel/91yp.jpg",
              "channelId": 100
            },
            "document": {
              "postDate": "2018-03-14 00:00:00",
              "author": "美频",
              "brands": []
            },
            "mp": {
              "id": 188,
              "type": 0,
              "topicId": 995249,
              "upTimes": 0,
              "mpCategoryId": 204
            },
            "mpdownloads": [],
            "mpCategory": {
              "id": 204,
              "parentId": 18,
              "type": 2,
              "title": "硬件\\驱动\\机架\\系统",
              "parent": {
                "id": 18,
                "parentId": 1,
                "type": 1,
                "title": "6NANO",
                "parent": {
                  "id": 1,
                  "parentId": 0,
                  "type": 0,
                  "title": "声卡"
                },
                "brandId": 6,
                "brandName": "紫罗兰"
              }
            },
            "imageSingle": false,
            "imageRotation": false,
            "liked": 0,
            "favorite": 0,
            "post": {
              "id": 1388640,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "modified": "2018-04-04 14:02:20",
              "parentId": 0,
              "topicId": 995249,
              "priority": 0,
              "language": 1,
              "categories": [
                "常用教程"
              ],
              "tags": [],
              "features": [
                {
                  "_name": "systems",
                  "_value": "WinXP/Win7/Win8/Vista"
                }
              ],
              "title": "6NANO 硬件安装",
              "description": "将文件下载放在桌面上，不要解压，不要安装，联系客服人员。",
              "content": "<div> \n \n <h5>软件简介</h5> \n <div>  \n  <div> \n   <img src=\"http://static.budee.com/yyren/image/14/50/3280484.jpg\"> \n   <br> \n   <br> &nbsp; \n  </div> \n </div> \n <h5>下载地址</h5> \n <div> \n  <ul> \n   <li><a href=\"http://91yp-huadong2-a.91yp.cn/Release/Full_91Setup_9.0.0.6.exe\"><img src=\"http://static.budee.com/yyren/image/13/50/3280288.jpg\"></a></li> \n   <li>将文件下载放在桌面上，不要解压，不要安装，联系客服人员。</li> \n  </ul> \n  <div>  \n  </div> \n </div> \n</div>",
              "postTypeValue": "爬取",
              "postType": 1
            },
            "thumbs": 0,
            "forumName": "美频技术支持",
            "topicTypeValue": "正常"
          }
        }

### 增加/修改 文章 [POST]

+ Description
    + [MUST] Authenticated
    + [MUST] ROLE_ADMIN | MP_ROLE_ADMIN

+ Parameters
    + forumId 必填，7：美频技术支持 8：美频行业新闻
    + categoryId 当forumId=7时必填，3978：常见问题，3979：知识库，3980：产品教程，当forumId=8时不填
    + seedId 必填123
    + mp.type 必填，0：图文，1：视频
    + mp.mpCategoryId
    + post.title - 必填
    + post.description
    + post.content - 必填
    + posts.tags
    + document.postDate
    + document.author
    + attachments
        + id 图片id
    + coverImages
        + id 图片id
        + displayOrder 排序
    + id 修改时必填，添加时必不填
    + post.creator - 修改时必填，添加时必不填

+ 新增常见问题Request (application/json)
    
        {
              "data":{
                  "forumId":7,
                  "seedId":123,
                  "categoryId":3978,
                  "mp":{
                      "type":0
                  },
                  "post":{
                      "title":"问题文章2",
                      "description":"问题文章2",
                      "content":"问题文章1",
                      "tags":[
                              "问题2","文章","测试"
                          ]
                  },
                  "attachments":[
                        {
                            "id":3280763
                        },
                        {
                            "id":3280764
                        }
                      ],
                    "coverImages":[
                            {
                                "id":3280763,
                                "displayOrder":1
                            },
                            {
                                "id":3280764,
                                "displayOrder":3
                            },
                            {
                                "id":3280765,
                                "displayOrder":2
                            }
                        ]
              }
          }
+ 新增知识库Request (application/json)

        {
            "data":{
                "forumId":7,
                "seedId":123,
                "categoryId":3979,
                "mp":{
                    "type":0
                },
                "post":{
                    "title":"知识库文章1",
                    "description":"知识库文章1",
                    "content":"知识库文章1",
                    "tags":[
                            "知识库","文章","测试"
                        ]
                }
            }
        }
+ 新增产品教程Request (application/json)

        {
            "data":{
                "forumId":7,
                "seedId":123,
                "categoryId":3980,
                "mp":{
                    "type":0,
                    "mpCategoryId":173
                },
                "post":{
                    "title":"产品教程文章1",
                    "description":"产品教程文章1",
                    "content":"产品教程文章1",
                    "tags":[
                            "产品教程","文章","测试"
                        ]
                }
            }
        }
+ 新增行业新闻Request (application/json)

        {
            "data":{
                "forumId":8,
                "seedId":123,
                "mp":{
                    "type":0
                },
                "post":{
                    "title":"行业新闻文章1",
                    "description":"行业新闻文章1",
                    "content":"行业新闻文章1",
                    "tags":[
                            "行业","新闻","测试"
                        ]
                }
            }
        }
+ 修改常见问题Request (application/json)
    
        {
            "data":{
                "id":996853,
                "forumId":7,
                "seedId":123,
                "categoryId":3978,
                "mp":{
                    "type":0
                },
                "post":{
                    "title":"问题文章1",
                    "description":"问题文章1",
                    "content":"问题文章1",
                    "tags":[
                            "问题","文章","测试"
                        ],
                    "creator":1031
                }
            }
        }
+ 修改知识库Request (application/json)

        {
            "data":{
                "id":996855,
                "forumId":7,
                "seedId":123,
                "categoryId":3979,
                "mp":{
                    "type":0
                },
                "post":{
                    "title":"知识库文章1",
                    "description":"知识库文章1",
                    "content":"知识库文章1",
                    "tags":[
                            "知识库","文章","测试"
                        ],
                    "creator":1031
                }
            }
        }
+ 修改产品教程Request (application/json)

        {
            "data":{
                "id":996856,
                "forumId":7,
                "seedId":123,
                "categoryId":3980,
                "mp":{
                    "type":0,
                    "mpCategoryId":173
                },
                "post":{
                    "title":"产品教程文章1",
                    "description":"产品教程文章1",
                    "content":"产品教程文章1",
                    "tags":[
                            "产品教程","文章","测试"
                        ],
                    "creator":1031
                }
            }
        }
+ 修改行业新闻Request (application/json)

        {
            "data":{
                "id":996857,
                "forumId":8,
                "seedId":123,
                "mp":{
                    "type":0
                },
                "post":{
                    "title":"行业新闻文章1",
                    "description":"行业新闻文章1",
                    "content":"行业新闻文章1",
                    "tags":[
                            "行业","新闻","测试"
                        ],
                    "creator":1031
                }
            }
        }
### 删除文章 [DELETE] /mp/topics/{id}
+ Description
    + [MUST] Authenticated
    + [MUST] ROLE_ADMIN | MP_ROLE_ADMIN

+ Response 204 (application/json)

### 置顶文章 [GET] /mp/topics/top/{id}?upTimes=1
+ Description
    + [MUST] Authenticated
    + [MUST] ROLE_ADMIN | MP_ROLE_ADMIN
+ Parameters
    + upTimes - 置顶系数，正数 | 负数
+ Response 200 (application/json)

## 快速下载分类管理
### 增加分类 [POST] /mpDownloadCategories

+ Description
    + [MUST] Authenticated
    + [MUST] ROLE_ADMIN | MP_ROLE_ADMIN
+ Parameters
    + categoryTitle - 必填
+ 新增Request (application/json)

        {
            "data":{
                "categoryTitle":"wo'jiu'shi我就是 kuai'su'xia'z快速下载 "
            }
        }
+ Response 201 (application/json)

        {
          "data": {
            "id": 6,
            "type": "mpDownloadCategories"
          }
        }

### 修改分类 [PATCH] /mpDownloadCategories/{id}

+ Description
    + [MUST] Authenticated
    + [MUST] ROLE_ADMIN | MP_ROLE_ADMIN

+ Parameters
    + categoryTitle - 必填
+ 修改Request (application/json)

        {
            "data":{
                "categoryTitle":"我就是快速下载 "
            }
        }
+ Response 200 (application/json)

### 分类列表 [GET] /mpDownloadCategories?filter[categoryTitle:like]=%25下载%25&sort=-modified

+ Parameters
    + filter[id]
    + filter[categoryTitle]
        + 模糊查询示例：filter[categoryTitle:like]=%25助手%25 （'%25'为'%'的转义）
    + sort -modified(从新到旧) | modified(从旧到新)
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
            "sort": [
              {
                "direction": "DESC",
                "property": "modified",
                "ignoreCase": false,
                "nullHandling": "NATIVE",
                "ascending": false,
                "descending": true
              }
            ]
          },
          "links": {
            "self": "/mpDownloadCategories?sort=-modified&filter[categoryTitle:like]=%下载%&page[number]=1&page[size]=10",
            "first": "/mpDownloadCategories?sort=-modified&filter[categoryTitle:like]=%下载%&page[number]=1&page[size]=10",
            "last": "/mpDownloadCategories?sort=-modified&filter[categoryTitle:like]=%下载%&page[number]=1&page[size]=10"
          },
          "data": [
            {
              "id": 6,
              "enabled": 1,
              "creator": 1031,
              "modifier": 1031,
              "created": "2018-05-10 11:51:13",
              "modified": "2018-05-10 11:57:27",
              "displayOrder": 0,
              "categoryTitle": "我就是快速下载 "
            },
            {
              "id": 3,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2018-05-03 16:44:01",
              "modified": "2018-05-03 16:44:01",
              "displayOrder": 0,
              "categoryTitle": "常用下载"
            },
            {
              "id": 2,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2018-05-03 16:43:57",
              "modified": "2018-05-03 16:43:57",
              "displayOrder": 0,
              "categoryTitle": "驱动下载"
            }
          ]
        }
### 删除分类 [DELETE] /mpDownloadCategories/{id}
+ Description
    + [MUST] Authenticated
    + [MUST] ROLE_ADMIN | MP_ROLE_ADMIN
+ Response 204 (application/json)

## 快速下载管理

### 增加快速下载 [POST] /mpDownloads

+ Description
    + [MUST] Authenticated
    + [MUST] ROLE_ADMIN | MP_ROLE_ADMIN

+ Parameters
    + categoryId - 必填
    + title - 必填
    + description
    + displayOrder
    + image
    + link - 必填
+ 新增Request (application/json)

        {
            "data":{
                "categoryId":8,
                "title":"yin'pin音频 zhu'shou助手",
                "displayOrder":2,
                "link":"http://static.budee.com/yyren/image/nginx-1.8.0.tar.gz"
            }
        }
+ Response 201 (application/json)

        {
          "data": {
            "id": 38,
            "type": "mpDownloads"
          }
        }
### 修改快速下载 [PATCH] /mpDownloads/{id}

+ Description
    + [MUST] Authenticated
    + [MUST] ROLE_ADMIN | MP_ROLE_ADMIN

+ Parameters
    + categoryId
    + title - 必填
    + description
    + displayOrder
    + image
    + link - 必填
+ 修改Request (application/json)

        {
            "data":{
                "title":"音频助手",
                "displayOrder":1,
                "link":"http://static.budee.com/yyren/image/nginx-1.8.0.tar.gz"
            }
        }
+ Response 200 (application/json)

### 快速下载列表 [GET] /mpDownloads?filter[categoryId]=6&&filter[title:like]=%25助手%25&sort=-modified

+ Parameters
    + filter[categoryId]
    + filter[id]
    + filter[title]
        + 模糊查询示例：filter[title:like]=%25助手%25 （'%25'为'%'的转义）
    + sort -modified(从新到旧) | modified(从旧到新)
+ Response 200 (application/json)

        {
          "meta": {
            "totalPages": 1,
            "totalElements": 1,
            "size": 10,
            "number": 1,
            "numberOfElements": 1,
            "first": true,
            "last": true,
            "sort": [
              {
                "direction": "DESC",
                "property": "modified",
                "ignoreCase": false,
                "nullHandling": "NATIVE",
                "ascending": false,
                "descending": true
              }
            ]
          },
          "links": {
            "self": "/mpDownloads?filter[categoryId]=6&sort=-modified&page[number]=1&page[size]=10",
            "first": "/mpDownloads?filter[categoryId]=6&sort=-modified&page[number]=1&page[size]=10",
            "last": "/mpDownloads?filter[categoryId]=6&sort=-modified&page[number]=1&page[size]=10"
          },
          "data": [
            {
              "id": 38,
              "enabled": 1,
              "creator": 1031,
              "modifier": 1031,
              "created": "2018-05-10 12:34:48",
              "modified": "2018-05-10 12:37:05",
              "categoryId": 6,
              "displayOrder": 1,
              "title": "音频助手",
              "link": "http://static.budee.com/yyren/image/nginx-1.8.0.tar.gz",
              "times": 0
            }
          ]
        }
### 快速下载详情 [GET] /mpDownloads/{id}
+ Response 200 (application/json)

        {
          "data": {
            "id": 38,
            "enabled": 1,
            "creator": 1031,
            "modifier": 1031,
            "created": "2018-05-10 12:34:48",
            "modified": "2018-05-10 12:37:05",
            "categoryId": 6,
            "displayOrder": 1,
            "title": "音频助手",
            "link": "http://static.budee.com/yyren/image/nginx-1.8.0.tar.gz",
            "times": 0,
            "categoryTitle": "我就是快速下载 "
          }
        }
### 删除快速下载 [DELETE] /mpDownloads/{id}
+ Description
    + [MUST] Authenticated
    + [MUST] ROLE_ADMIN | MP_ROLE_ADMIN
+ Response 204 (application/json)

### 文件上传 [POST] /admin/Attachments/uploadFile
+ Description
    + [MUST] Authenticated
    + [MUST] ROLE_ADMIN | MP_ROLE_ADMIN
    + 文件不能超过10M
    + 格式限定：exe | zip | rar
+ Parameters
    + type 必填 0/1/2 : 音频助手/驱动/软件
    + file 必填
+ Response 200 (application/json)
    
        {
          "data": "upload successful!"
        }
