# 美频

美频 API 

+ 2018年3月30日
    + 初始化
+ 2018年3月31日
    + 后台品牌管理api


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
    + mpDownloads - 美频下载
        + id (long)
        + type (int) - 0：91助手，1：驱动下载，2：常用软件
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
    + topicsMp - 美频文章相关数据
        + id (long)
        + type (int) - 类型：0：图文，1：视频
        + topicId (long) - 主题标识
        + upTimes (int) - 置顶次数
        + mpCategoryId (long) - 美频教程分类标识
        + enabled (int) - 是否可用 0/1:否/是
        + creator (long)
        + modifier (long)
        + created (date)
        + modified (date)

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
+ 行业新闻轮播图 /mp/topics/hotnews
    + params
        + filter[forum] 必填8
        + page[size] 根据需求填写
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
+ 推荐行业新闻 (GET)/topics/search?filter[forum]=8&fiter[items.saleRank:gt]=0&agg[size]=-1&sort=-items.saleRank

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
                "images":"tupian.jpg",
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
