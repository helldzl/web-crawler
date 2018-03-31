# 美频

美频 API 

+ 2018年3月30日
    + 初始化

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
+ 常见问题|知识库 (GET)/mp/topics/supports?fromDays=30&filter[forum]=7&filter[categoryId]=xx&page[size]=15
    + params
        + fromDays 从何时开始的点击量排序，根据现在的需求填30就可以
        + filter[forum] 必填7
        + filter[categoryId] 待定（这个要注意，测试服务器和生产服务器可能不一样）
        + page[size] 根据需求填写
+ 选择品牌 (GET)/mpBrands
+ 根据品牌查询一级分类及二级分类（产品型号） (GET)/mpCategories?filter[brandId]=1

### 技术支持页
+ 常见问题|知识库轮播图 (接口同首页常见问题|知识库)
+ 轮播图下方数据 (GET)/topics/search?filter[forum]=7&page[number]=1&page[size]=10&agg[size]=-1&sort=-created
    + params
        + filter[forum] 必填7
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
