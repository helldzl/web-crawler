# topics-2.3.0

2.3.0 mifan API 

+ 2018年3月9日
    + 初始化
    
## 48个品牌名（搜索引擎认识的）
    Akai,AKG,Alesis,API Audio,Allen & Heath,Apogee,Avid,B&O Play,Blue,Bettermaker,Burl Audio,Chandler Limited,Crown,DPA,DiGiGrid,EAW,EV,Empirical Labs,Fender,Genelec,Gibson,Heritage Audio,Icon,JBL,K&M,Lexicon,MAGIC-V,MOTU,Manley,Marshall,Martin Guitars,Pearl,Pioneer,PreSonus,QSC,Quested,Roland,RØDE Microphones,Sennheiser,Shadow Hills Industries,Steinberg,T-Rex,TC Electronic,Telefunken,Trinnov,Violet,Waves,Yamaha

## 搜索结果页面
### 亮点产品
+ 热门 /topics/search?filter[q]=我的关键字&filter[forum]=1&filter[items.saleRank:ge]=1&agg[size]=-1
+ 新品 /topics/search?filter[q]=我的关键字风&filter[forum]=1&filter[created:ge]=2018-02-22&agg[size]=-1
    + 说明：filter[created:ge]参数请算出一个月前的日期

## 首页
### 亮点产品
+ 新品 [/topics/search?filter[forum]=1&filter[items.seedId]=11&sort=-created&page[size]=15&agg[size]=-1] 
+ 热门 [/topics/search?filter[forum]=1&sort=items.saleRank&page[size]=15&agg[size]=-1] 
### (GET) 48个热门品牌 [/brands/hot]

+ Response 200 (application/json)

        {
          "data": [
            {
              "id": 400663,
              "name": "Akai",
              "logo": "http://static.budee.com/yyren/image/113/28/1864140.jpg",
              "rating": 0,
              "reviews": 0,
              "top": false
            },
            {
              "id": 400668,
              "name": "AKG",
              "logo": "http://static.budee.com/yyren/image/113/28/1864145.jpg",
              "rating": 0,
              "reviews": 0,
              "top": false
            }
          ]
        }


## 一级分类详情页面
### 亮点产品
+ 新品 /topics/search?filter[category]=麦克风&filter[forum]=1&sort=-created&page[size]=15&agg[size]=-1
+ 热门 /topics/search?filter[category]=麦克风&filter[forum]=1&sort=saleRank&page[size]=15&agg[size]=-1
### 热门品牌
    /topics/search?page[size]=0&filter[forumId]=1&filter[categoryId]=2961&aggregation[brand]=brand.name&filter[brand.name]=Akai,AKG,Alesis,API Audio,Allen %26 Heath,Apogee,Avid,B%26O Play,Blue,Bettermaker,Burl Audio,Chandler Limited,Crown,DPA,DiGiGrid,EAW,EV,Empirical Labs,Fender,Genelec,Gibson,Heritage Audio,Icon,JBL,K%26M,Lexicon,MAGIC-V,MOTU,Manley,Marshall,Martin Guitars,Pearl,Pioneer,PreSonus,QSC,Quested,Roland,RØDE Microphones,Sennheiser,Shadow Hills Industries,Steinberg,T-Rex,TC Electronic,Telefunken,Trinnov,Violet,Waves,Yamaha

## 二级分类详情页面
### 新闻评测
    + 新闻 /topics/search?filter[q]=无线麦克风&filter[forum]=3&page[size]=1&agg[size]=-1
    + 评测 /topics/search?filter[q]=无线麦克风&filter[forum]=4&page[size]=4&agg[size]=-1 
### 产品列表
    /topics/search?filter[category]=无线麦克风&filter[forum]=1&page[number]=1&page[size]=15&sort=-created&agg[size]=-1
### 亮点产品
+ 热门 /topics/search?filter[category]=无线麦克风&filter[forum]=1&filter[items.seedId]=11&page[size]=15&sort=saleRank&agg[size]=-1
+ 新品 /topics/search?filter[category]=无线麦克风&filter[forum]=1&filter[items.seedId]=11&page[size]=15&sort=-created&agg[size]=-1
### 热门品牌
    /topics/search?page[size]=0&filter[forumId]=1&filter[category]=无线麦克风&aggregation[brand]=brand.name&filter[brand.name]=Akai,AKG,Alesis,API Audio,Allen %26 Heath,Apogee,Avid,B%26O Play,Blue,Bettermaker,Burl Audio,Chandler Limited,Crown,DPA,DiGiGrid,EAW,EV,Empirical Labs,Fender,Genelec,Gibson,Heritage Audio,Icon,JBL,K%26M,Lexicon,MAGIC-V,MOTU,Manley,Marshall,Martin Guitars,Pearl,Pioneer,PreSonus,QSC,Quested,Roland,RØDE Microphones,Sennheiser,Shadow Hills Industries,Steinberg,T-Rex,TC Electronic,Telefunken,Trinnov,Violet,Waves,Yamaha
### 其他分类 [/forumCategories/otherChildren?parentId=1997&excludeId=2342]
+ Response 200 (application/json)

        {
          "data": {
            "id": 1997,
            "enabled": 1,
            "forumId": 1,
            "rootId": 1997,
            "parentId": 0,
            "title": "Microphones",
            "filename": "http://static.budee.com/yyren/image/category/1997.jpg",
            "path": "1997",
            "depth": 1,
            "leaf": 0,
            "displayOrder": 16,
            "titleChinese": "麦克风",
            "children": [
              {
                "id": 4223,
                "enabled": 1,
                "forumId": 1,
                "rootId": 1997,
                "parentId": 1997,
                "title": "Live Microphones",
                "filename": "http://static.budee.com/yyren/image/241/14/979421.jpg",
                "path": "1997.3975",
                "depth": 2,
                "leaf": 1,
                "displayOrder": 0,
                "titleChinese": "现场麦克风",
                "children": [],
                "topics": []
              },
              {
                "id": 2338,
                "enabled": 1,
                "forumId": 1,
                "rootId": 1997,
                "parentId": 1997,
                "title": "Vocal Mics",
                "filename": "http://static.budee.com/yyren/image/244/13/914532.jpg",
                "path": "1997.2338",
                "depth": 2,
                "leaf": 0,
                "displayOrder": 0,
                "titleChinese": "声乐麦克风",
                "children": [],
                "topics": []
              }
            ],
            "topics": []
          }
        }

## 品牌二级分类详情页面 （例：AKG无线麦克风）
### 新闻评测
    + 新闻 /topics/search?filter[q]=yamaha无线麦克风&filter[forum]=3&page[size]=1&agg[size]=-1
    + 评测 /topics/search?filter[q]=yamaha无线麦克风&filter[forum]=4&page[size]=4&agg[size]=-1
### 产品列表
    /topics/search?filter[category]=无线麦克风&filter[brand]=AKG&filter[forum]=1&sort=-created&page[number]=1&page[size]=15&agg[size]=-1
### 亮点产品
+ 热门 /topics/search?filter[category]=无线麦克风&filter[brand]=AKG&filter[forum]=1&filter[items.seedId]=11&sort=saleRank&page[size]=15&agg[size]=-1
+ 新品 /topics/search?filter[category]=无线麦克风&filter[brand]=AKG&filter[forum]=1&filter[items.seedId]=11&sort=-created&page[size]=15&agg[size]=-1
### 其他分类（注意：filter[level_0.cn.raw]的值是一级分类，此接口是根据品牌和一级分类聚合二级分类）
    /topics/search?page[size]=0&filter[forumId]=1&filter[brand.name]=Yamaha&filter[level_0.cn.raw]=吉他/贝斯&agg[group]=false&agg[image]=true&aggregation[category]=level_1.raw
    
### 热门品牌 （从48个热门品牌中筛选包含该分类的品牌）
    /topics/search?page[size]=0&filter[forumId]=1&filter[category]=无线麦克风&aggregation[brand]=brand.name&filter[brand.name]=Akai,AKG,Alesis,API Audio,Allen %26 Heath,Apogee,Avid,B%26O Play,Blue,Bettermaker,Burl Audio,Chandler Limited,Crown,DPA,DiGiGrid,EAW,EV,Empirical Labs,Fender,Genelec,Gibson,Heritage Audio,Icon,JBL,K%26M,Lexicon,MAGIC-V,MOTU,Manley,Marshall,Martin Guitars,Pearl,Pioneer,PreSonus,QSC,Quested,Roland,RØDE Microphones,Sennheiser,Shadow Hills Industries,Steinberg,T-Rex,TC Electronic,Telefunken,Trinnov,Violet,Waves,Yamaha


## 品牌详情页
### 亮点产品
+ 新品 [/topics/search?filter[forum]=1&filter[items.seedId]=11&filter[brand]=Blue&sort=-created&page[size]=15&agg[size]=-1]
+ 热门 [/topics/search?filter[forum]=1&filter[brand]=Blue&sort=items.saleRank&page[size]=15&agg[size]=-1] 
### (GET) 品牌经典评测 [/fewTopics/hotByBrandsForReviews?brands=akai,akg,blue,gibson,martin guitars,yamaha,alesis,marshall,roland,avid,sennheiser,k&m&filter[forum]=4&size=10]

+ Response 200 (application/json)

        {
          "data": [
            {
              "id": 638754,
              "forumId": 4,
              "forumName": "评测",
              "topicType": 0,
              "topicTypeValue": "正常",
              "imageSingle": false,
              "imageRotation": false,
              "creator": 0,
              "created": "2018-01-12 17:33:40",
              "modified": "2018-02-03 14:22:47",
              "reviews": 0,
              "replies": 0,
              "thumbsUp": 0,
              "thumbsDown": 0,
              "thumbs": 0,
              "liked": 0,
              "favorite": 0,
              "brand": {
                "reviews": 0,
                "top": false,
                "name": "rode,blue",
                "rating": 0,
                "logo": null,
                "id": 0
              },
              "rotations": [],
              "images": [
                {
                  "filename": "http://static.budee.com/yyren/image/183/39/2602971.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/183/39/2602972.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/184/39/2603051.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/184/39/2603052.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/184/39/2603053.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/184/39/2603054.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/184/39/2603055.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/184/39/2603056.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/184/39/2603057.jpg"
                }
              ],
              "from": {
                "image": "http://static.budee.com/yyren/image/channel/micreviews.jpg",
                "seedId": 27,
                "origin": "https://www.micreviews.com/guides/top-10-best-microphones-for-podcasting",
                "host": "http://www.micreviews.com",
                "rating": 0,
                "source": "micreviews",
                "channelId": 32
              },
              "post": {
                "postType": 1,
                "postTypeValue": "爬取",
                "title": "The Top 10 Best Microphones for Podcasting",
                "description": "The power of podcasting is a beautiful thing. Nowadays with technology, just about everybody with a decent computer and solid internet connection can ...",
                "categories": [],
                "tags": [
                  "guide",
                  "podcast",
                  "top 10"
                ]
              },
              "document": {
                "postDate": "2018-01-12",
                "author": "Sean"
              },
              "similarities": []
            },
            {
              "id": 450409,
              "forumId": 4,
              "forumName": "评测",
              "topicType": 0,
              "topicTypeValue": "正常",
              "imageSingle": false,
              "imageRotation": false,
              "creator": 0,
              "created": "2003-08-08 00:17:23",
              "modified": "2018-01-17 20:17:49",
              "reviews": 0,
              "replies": 0,
              "thumbsUp": 0,
              "thumbsDown": 0,
              "thumbs": 0,
              "liked": 0,
              "favorite": 0,
              "brand": {
                "reviews": 0,
                "top": false,
                "name": "yamaha",
                "rating": 0,
                "logo": null,
                "id": 0
              },
              "rotations": [],
              "images": [
                {
                  "filename": "http://static.budee.com/yyren/image/137/29/1935834.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/137/29/1935839.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/137/29/1935842.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/137/29/1935845.jpg"
                }
              ],
              "from": {
                "image": "http://static.budee.com/yyren/image/channel/sweetwater.jpg",
                "seedId": 29,
                "origin": "https://www.sweetwater.com/insync/yamaha-motif-6-review/",
                "host": "https://www.sweetwater.com",
                "rating": 0,
                "source": "Sweetwater",
                "channelId": 7
              },
              "post": {
                "postType": 1,
                "postTypeValue": "爬取",
                "title": "Yamaha Motif 6 Review",
                "description": "The MOTIF6 by Yamaha is an amazing music production workstation loaded with tons of extremely useful sounds for musicians, composers, or sound designe...",
                "categories": [],
                "tags": [
                  "Product Reviews",
                  "Keyboard",
                  "Motif6",
                  "Yamaha"
                ]
              },
              "document": {
                "postDate": "2003-08-08",
                "author": "Marty Weiser"
              },
              "similarities": []
            }
          ]
        }
        
### (GET) 品牌详情页的四个相关咨询 [/fewTopics/newsForBrands?brands=akai] 

+ Response 200 (application/json)

        {
          "data": [
            {
              "id": 507443,
              "forumId": 3,
              "forumName": "新闻",
              "topicType": 0,
              "topicTypeValue": "正常",
              "imageSingle": false,
              "imageRotation": false,
              "creator": 0,
              "created": "2017-06-28 16:23:04",
              "modified": "2018-01-17 20:18:03",
              "reviews": 0,
              "replies": 0,
              "thumbsUp": 0,
              "thumbsDown": 0,
              "thumbs": 0,
              "liked": 0,
              "favorite": 0,
              "brand": {
                "reviews": 0,
                "top": false,
                "name": "akai",
                "rating": 0,
                "logo": null,
                "id": 0
              },
              "rotations": [],
              "images": [
                {
                  "filename": "http://static.budee.com/yyren/image/40/32/2107425.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/40/32/2107426.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/40/32/2107427.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/40/32/2107428.jpg"
                }
              ],
              "from": {
                "image": "http://static.budee.com/yyren/image/channel/ingping.jpg",
                "seedId": 80,
                "origin": "https://zx.ingping.com/c_1/19152.html",
                "host": "https://zx.ingping.com",
                "rating": 0,
                "source": "音平资讯",
                "channelId": 66
              },
              "post": {
                "postType": 1,
                "postTypeValue": "爬取",
                "title": "Akai发布Advance系列MIDI键盘控制器",
                "description": "Akai发布Advance系列MIDI键盘控制器摘要：Akai在本届展会将会发布带有插件和集成DAW（数字音频工作站）的新系列MIDI控制键盘。新系列键盘具有25、49和61键版本，全部配备高品质控制功能，可用于几百种虚拟乐器和DAW操作。三款MIDI键盘.",
                "categories": [
                  "行业资讯AKAI键盘;AKAI"
                ],
                "tags": [
                  "AKAI键盘",
                  "AKAI",
                  "AKAI键盘",
                  "AKAI",
                  "AKAI",
                  "AKAI键盘",
                  "AKAI",
                  "MIDI键盘",
                  "AKAI",
                  "AKAI"
                ]
              },
              "document": {
                "postDate": "2017-06-28",
                "author": "音平资讯"
              },
              "similarities": []
            },
            {
              "id": 507565,
              "forumId": 3,
              "forumName": "新闻",
              "topicType": 0,
              "topicTypeValue": "正常",
              "imageSingle": false,
              "imageRotation": false,
              "creator": 0,
              "created": "2017-06-28 14:24:55",
              "modified": "2018-01-17 20:18:03",
              "reviews": 0,
              "replies": 0,
              "thumbsUp": 0,
              "thumbsDown": 0,
              "thumbs": 0,
              "liked": 0,
              "favorite": 0,
              "brand": {
                "reviews": 0,
                "top": false,
                "name": "serato,akai",
                "rating": 0,
                "logo": null,
                "id": 0
              },
              "rotations": [],
              "images": [
                {
                  "filename": "http://static.budee.com/yyren/image/42/32/2108034.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/42/32/2108035.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/42/32/2108036.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/42/32/2108037.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/42/32/2108038.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/42/32/2108039.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/42/32/2108040.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/42/32/2108041.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/42/32/2108042.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/42/32/2108043.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/42/32/2108044.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/42/32/2108045.jpg"
                }
              ],
              "from": {
                "image": "http://static.budee.com/yyren/image/channel/ingping.jpg",
                "seedId": 80,
                "origin": "https://zx.ingping.com/c_1/19228.html",
                "host": "https://zx.ingping.com",
                "rating": 0,
                "source": "音平资讯",
                "channelId": 66
              },
              "post": {
                "postType": 1,
                "postTypeValue": "爬取",
                "title": "AKAI 投入 Serato DJ 怀抱，推出专用控制器/声卡 AFX 和 AMX",
                "description": "AKAI 投入 Serato DJ 怀抱，推出专用控制器/声卡 AFX 和 AMX摘要：AMX是一个针对Serato DJ软件设计的调音台控制器，同时内置有USB的24bit/96kHz音频接口，支持Serato NoiseMap控制信号。AFX是一个同时适合turntablists和现。",
                "categories": [
                  "行业资讯DJ控制器"
                ],
                "tags": [
                  "DJ控制器",
                  "DJ控制器",
                  "DJ控制器",
                  "DJ控制器",
                  "DJ控制器",
                  "DJ控制器"
                ]
              },
              "document": {
                "postDate": "2017-06-28",
                "author": "音平资讯"
              },
              "similarities": []
            },
            {
              "id": 506453,
              "forumId": 4,
              "forumName": "评测",
              "topicType": 0,
              "topicTypeValue": "正常",
              "imageSingle": false,
              "imageRotation": false,
              "creator": 0,
              "created": "2017-05-16 03:01:30",
              "modified": "2018-01-17 20:18:03",
              "reviews": 0,
              "replies": 0,
              "thumbsUp": 0,
              "thumbsDown": 0,
              "thumbs": 0,
              "liked": 0,
              "favorite": 0,
              "brand": {
                "reviews": 0,
                "top": false,
                "name": "ableton,akai",
                "rating": 0,
                "logo": null,
                "id": 0
              },
              "rotations": [],
              "images": [
                {
                  "filename": "http://static.budee.com/yyren/image/25/32/2103725.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/25/32/2103726.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/25/32/2103727.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/25/32/2103728.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/25/32/2103729.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/25/32/2103730.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/25/32/2103731.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/25/32/2103732.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/25/32/2103733.jpg"
                }
              ],
              "from": {
                "image": "http://static.budee.com/yyren/image/channel/ingping.jpg",
                "seedId": 80,
                "origin": "https://zx.ingping.com/c_2/7810.html",
                "host": "https://zx.ingping.com",
                "rating": 0,
                "source": "音平资讯",
                "channelId": 66
              },
              "post": {
                "postType": 1,
                "postTypeValue": "爬取",
                "title": "Akai APC20 Ableton Live 专用控制器评测",
                "description": "Akai APC20 Ableton Live 专用控制器评测摘要：APC 20是AKAI在APC 40之后推出的又一款Ableton Live控制器，它的尺寸有所缩小，但是某些功能上有所优化。　　  图1：APC 20的包装 　　  图2：开包以后的内容 　",
                "categories": [
                  "产品评测AKAI;MIDI键盘"
                ],
                "tags": [
                  "AKAI",
                  "MIDI键盘",
                  "硬件新闻",
                  "MIDI键盘",
                  "软件使用教程",
                  "MIDI键盘",
                  "品牌新闻",
                  "MIDI键盘",
                  "品牌新闻",
                  "MIDI键盘",
                  "品牌新闻",
                  "MIDI键盘"
                ]
              },
              "document": {
                "postDate": "2017-05-16",
                "author": "音平资讯"
              },
              "similarities": []
            },
            {
              "id": 507516,
              "forumId": 4,
              "forumName": "评测",
              "topicType": 0,
              "topicTypeValue": "正常",
              "imageSingle": false,
              "imageRotation": false,
              "creator": 0,
              "created": "2017-03-23 00:06:20",
              "modified": "2018-01-17 20:18:03",
              "reviews": 0,
              "replies": 0,
              "thumbsUp": 0,
              "thumbsDown": 0,
              "thumbs": 0,
              "liked": 0,
              "favorite": 0,
              "brand": {
                "reviews": 0,
                "top": false,
                "name": "akai",
                "rating": 0,
                "logo": null,
                "id": 0
              },
              "rotations": [],
              "images": [
                {
                  "filename": "http://static.budee.com/yyren/image/41/32/2107692.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/41/32/2107693.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/41/32/2107694.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/41/32/2107695.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/41/32/2107696.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/41/32/2107697.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/41/32/2107698.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/41/32/2107699.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/41/32/2107700.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/41/32/2107701.jpg"
                },
                {
                  "filename": "http://static.budee.com/yyren/image/41/32/2107702.jpg"
                }
              ],
              "from": {
                "image": "http://static.budee.com/yyren/image/channel/ingping.jpg",
                "seedId": 80,
                "origin": "https://zx.ingping.com/c_2/18107.html",
                "host": "https://zx.ingping.com",
                "rating": 0,
                "source": "音平资讯",
                "channelId": 66
              },
              "post": {
                "postType": 1,
                "postTypeValue": "爬取",
                "title": "Akai 一体化工作站 MPC X 一时间上手评测",
                "description": "Akai 一体化工作站 MPC X 一时间上手评测摘要：Akai 何时会推出独立版的 MPC 一度成为了业内较大的茶余话题，只不过没想到这个产品就这样到来了。在这次的 NAMM 上我们也见到了传说中的 MPC 一体机之真身 —— MPC X。",
                "categories": [
                  "产品评测"
                ],
                "tags": []
              },
              "document": {
                "postDate": "2017-03-23",
                "author": "音平资讯"
              },
              "similarities": []
            }
          ]
        }

