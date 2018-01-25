# 用户微服务

{version} = "", 即用户微服务因为已经单独拆分出来了，暂时版本号为空；

|	原 API	|	新 API
|	 -----	|	 -----
|	/oauth/token/refresh	|	{version}/user/oauth/token/refresh
|	/oauth/check.jpg	|	{version}/user/oauth/check.jpg
|	/oauth/token	|	{version}/user/oauth/token
|	/oauth/phone/bind	|	{version}/user/oauth/phone/bind
|	/oauth/phone	|	{version}/user/oauth/phone
|	/oauth/logout	|	{version}/user/oauth/logout
|	/user/authorities/roles/{roleId}	|	{version}/user/authorities/roles/{roleId}
|	/user/authorities/{id}	|	{version}/user/authorities/{id}
|	/user/authorities	|	{version}/user/authorities
|	/user/groups/{groupId}/roles	|	{version}/user/groups/{groupId}/roles
|	/user/groups/{id}	|	{version}/user/groups/{id}
|	/user/groups	|	{version}/user/groups
|	/user/groups/sites/{siteId}/users/{userId}	|	{version}/user/groups/sites/{siteId}/users/{userId}
|	/user/roles/{roleId}/authorities	|	{version}/user/roles/{roleId}/authorities
|	/user/roles/sites/{siteId}/users/{userId}	|	{version}/user/roles/sites/{siteId}/users/{userId}
|	/user/roles/{id}	|	{version}/user/roles/{id}
|	/user/roles	|	{version}/user/roles
|	/user/roles/groups/{groupId}	|	{version}/user/roles/groups/{groupId}
|	/user/sites/{id}	|	{version}/user/sites/{id}
|	/user/sites	|	{version}/user/sites
|	/register/check.jpg	|	{version}/user/register/check.jpg
|	/register/send_sms_code	|	{version}/user/register/send_sms_code
|	/user/userAccounts	|	{version}/user/userAccounts
|	/api/addresses/{id}	|	{version}/user/addresses/{id}
|	/api/addresses	|	{version}/user/addresses
|	/api/addresses/admin	|	{version}/user/addresses/admin
|	/api/invitations	|	{version}/user/invitations
|	/api/grains	|	{version}/user/grains
|	/api/profiles/{id}	|	{version}/user/profiles/{id}
|	/api/profiles	|	{version}/user/profiles
|	/api/profiles/admin	|	{version}/user/profiles/admin
|	/api/profiles/{id}/admin	|	{version}/user/profiles/{id}/admin
|	/api/users	|	{version}/user/users
|	/api/users/{id}	|	{version}/user/users/{id}
|	/api/users/sites/{siteId}/users/{userId}/roles	|	{version}/user/users/sites/{siteId}/users/{userId}/roles
|	/api/users/backpwd	|	{version}/user/users/backpwd
|	/api/usersexist	|	{version}/user/users/exist
|	/api/users/sites/{siteId}/users/{userId}/groups	|	{version}/user/users/sites/{siteId}/users/{userId}/groups
|	/wechat/signature	|	{version}/user/wechat/signature
|	/oauth/weChat	|	{version}/user/oauth/weChat
|	/zhangyongwei	|	{version}/user/zhangyongwei
|	/oauth/weChat/bind	|	{version}/user/oauth/weChat/bind
|	/isFollow	|	{version}/user/isFollow

# 米饭微服务（支持微服务，主题微服务，抽奖微服务）

{version} = "/v1", 米饭微服务包含多个未拆分的服务，统一设置一个版本号。

## 支持微服务 /support

|	原 API	|	新 API	|
|	 -----	|	 -----	|
|	/commentConfs/{id}	|	{version}/support/commentConfs/{id}	|
|	/commentConfs	|	{version}/support/commentConfs	|
|	/comments/{id}	|	{version}/support/comments/{id}	|
|	/comments	|	{version}/support/comments	|
|	/comments/theme	|	{version}/support/comments/theme	|
|	/comments/hots	|	{version}/support/comments/hots	|
|	/eventLogs	|	{version}/support/eventLogs	|
|	/eventLogs/{id}	|	{version}/support/eventLogs/{id}	|
|	/support/eventDics/{id}	|	{version}/support/eventDics/{id}	|
|	/support/eventDics	|	{version}/support/eventDics	|
|	/praises	|	{version}/support/praises	|
|	/tags/{id}	|	{version}/support/tags/{id}	|
|	/tags	|	{version}/support/tags	|
|	/article/ranks	|	{version}/support/ranks	|
|	/article/ranks/{key}	|	{version}/support/ranks/{key}	|
|	/article/ranks/scores	|	{version}/support/ranks/scores	|
|	/api/upload	|	{version}/support/upload	|

## 主题微服务 /topic

|	原 API	|	新 API	|
|	 -----	|	 -----	|
|	/brands/{name}	|	{version}/article/brands/{name}	|
|	/article/feedback/{id}	|	{version}/article/feedback/{id}	|
|	/article/feedback	|	{version}/article/feedback	|
|	/article/folders/{id}/compare	|	{version}/article/folders/{id}/compare	|
|	/article/folders/{id}	|	{version}/article/folders/{id}	|
|	/article/folders	|	{version}/article/folders	|
|	/article/forumCategories/{id}	|	{version}/article/forumCategories/{id}	|
|	/article/forumCategories	|	{version}/article/forumCategories	|
|	/article/forumCategories/mp/{id}	|	{version}/article/forumCategories/mp/{id}	|
|	/article/hopeTranslates	|	{version}/article/hopeTranslates	|
|	/article/hopeTranslates/{id}	|	{version}/article/hopeTranslates/{id}	|
|	/article/hopeTranslateExtends/{id}	|	{version}/article/hopeTranslateExtends/{id}	|
|	/article/hopeTranslateExtends	|	{version}/article/hopeTranslateExtends	|
|	/article/humanTranslates/{id}	|	{version}/article/humanTranslates/{id}	|
|	/article/humanTranslates	|	{version}/article/humanTranslates	|
|	/links/{id}	|	{version}/article/links/{id}	|
|	/links	|	{version}/article/links	|
|	/article/messages/{id}	|	{version}/article/messages/{id}	|
|	/article/messages	|	{version}/article/messages	|
|	/article/moderations	|	{version}/article/moderations	|
|	/article/moderations/audit/{id}	|	{version}/article/moderations/audit/{id}	|
|	/article/navigation/{id}	|	{version}/article/navigation/{id}	|
|	/article/navigation	|	{version}/article/navigation	|
|	/article/quartzJobs/{id}	|	{version}/article/quartzJobs/{id}	|
|	/article/quartzJobs	|	{version}/article/quartzJobs	|
|	/spider/statistics	|	{version}/article/spider/statistics	|
|	/spider/rabbitmq/connections	|	{version}/article/spider/rabbitmq/connections	|
|	/spider/statistics/topicsfetch/{seedId}	|	{version}/article/spider/statistics/topicsfetch/{seedId}	|
|	/topicsClusterings/{id}	|	{version}/article/topicsClusterings/{id}	|
|	/topicsClusterings	|	{version}/article/topicsClusterings	|
|	/topics/compare	|	{version}/article/topics/compare	|
|	/topics/{id}	|	{version}/article/topics/{id}	|
|	/topics/colors	|	{version}/article/topics/colors	|
|	/topics/search	|	{version}/article/topics/search	|
|	/topics/{id}/relates	|	{version}/article/topics/{id}/relates	|
|	/topics/favorites	|	{version}/article/topics/favorites	|
|	/topics/histories	|	{version}/article/topics/histories	|
|	/topics/hotKeywords	|	{version}/article/topics/hotKeywords	|
|	/topics/mpRecommend	|	{version}/article/topics/mpRecommend	|
|	/topics/mpHot	|	{version}/article/topics/mpHot	|
|	/topics/keywords	|	{version}/article/topics/keywords	|
|	/article/topicsModel/{id}	|	{version}/article/topicsModel/{id}	|
|	/article/topicsModel	|	{version}/article/topicsModel	|
|	/article/topicsModel/modelStatus	|	{version}/article/topicsModel/modelStatus	|
|	/article/translateTasks/{id}	|	{version}/article/translateTasks/{id}	|
|	/article/translateTasks	|	{version}/article/translateTasks	|
|	/article/translateTasks/translators/{id}	|	{version}/article/translateTasks/translators/{id}	|
|	/article/translateTasks/auditors/{id}	|	{version}/article/translateTasks/auditors/{id}	|
|	/article/translateTasks/auditors	|	{version}/article/translateTasks/auditors	|
|	/article/translateTasks/translators	|	{version}/article/translateTasks/translators	|
|	/users/{id}/relationships/{relationship:folders}/{sub:compare}	|	{version}/article/users/{id}/relationships/{relationship:folders}/{sub:compare}	|
|	/users/{id}/relationships/{relationship:folders}	|	{version}/article/users/{id}/relationships/{relationship:folders}	|
|	/article/usersFoldersCompare/{id}	|	{version}/article/usersFoldersCompare/{id}	|
|	/article/usersFoldersCompare	|	{version}/article/usersFoldersCompare	|
|	/users/{id}/relationships/{relationship:topics}/{sub:hide|like|report|favorite}	|	{version}/article/users/{id}/relationships/{relationship:topics}/{sub:hide|like|report|favorite}	|
|	/users/{id}/relationships/{relationship:topics}	|	{version}/article/users/{id}/relationships/{relationship:topics}	|
|	/users/relationships/topics/report/{id}	|	{version}/article/users/relationships/topics/report/{id}	|
|	/users/relationships/topics/report	|	{version}/article/users/relationships/topics/report	|
|	/article/votes/{id}	|	{version}/article/votes/{id}	|
|	/article/votes/report	|	{version}/article/votes/report	|
|	/article/votes/translate	|	{version}/article/votes/translate	|
|	/article/votes/option/{id}	|	{version}/article/votes/option/{id}	|
|	/article/votes/option	|	{version}/article/votes/option	|
|	/article/wordDictionary/{id}	|	{version}/article/wordDictionary/{id}	|
|	/article/wordDictionary	|	{version}/article/wordDictionary	|
|	/channels	|	{version}/article/channels	|
|	/channels/{id}	|	{version}/article/channels/{id}	|
|	/channels/users/{id}	|	{version}/article/channels/users/{id}	|
|	/channels/{id}/enabled/{enabled}	|	{version}/article/channels/{id}/enabled/{enabled}	|
|	/channels/{channelId}/seeds	|	{version}/article/channels/{channelId}/seeds	|
|	/users/{id}/relationships/{relationship:channels}/{sub:watch}	|	{version}/article/users/{id}/relationships/{relationship:channels}/{sub:watch}	|
|	/users/{id}/relationships/{relationship:channels}	|	{version}/article/users/{id}/relationships/{relationship:channels}	|
|	/article/admin/Attachments/upload	|	{version}/article/admin/Attachments/upload	|
|	/article/admin/Efss/{id}	|	{version}/article/admin/Efss/{id}	|
|	/article/admin/Efss	|	{version}/article/admin/Efss	|
|	/article/admin/Eqbs/{id}	|	{version}/article/admin/Eqbs/{id}	|
|	/article/admin/Eqbs	|	{version}/article/admin/Eqbs	|
|	/article/admin/Feedback/{id}	|	{version}/article/admin/Feedback/{id}	|
|	/article/admin/Feedback	|	{version}/article/admin/Feedback	|
|	/article/admin/Index/{id}	|	{version}/article/admin/Index/{id}	|
|	/article/admin/Index/cache/brand/{name}	|	{version}/article/admin/Index/cache/brand/{name}	|
|	/article/admin/Index	|	{version}/article/admin/Index	|
|	/article/admin/Index/batch	|	{version}/article/admin/Index/batch	|
|	/article/admin/Links/{id}	|	{version}/article/admin/Links/{id}	|
|	/article/admin/Links	|	{version}/article/admin/Links	|
|	/article/admin/Messages/{id}	|	{version}/article/admin/Messages/{id}	|
|	/article/admin/Messages	|	{version}/article/admin/Messages	|
|	/article/admin/Posts/enabled/{id}	|	{version}/article/admin/Posts/enabled/{id}	|
|	/article/admin/Posts/{id}	|	{version}/article/admin/Posts/{id}	|
|	/article/admin/Posts	|	{version}/article/admin/Posts	|
|	/article/admin/Posts/topic/{topicId}	|	{version}/article/admin/Posts/topic/{topicId}	|
|	/article/admin/Seeds/{id}	|	{version}/article/admin/Seeds/{id}	|
|	/article/admin/Seeds	|	{version}/article/admin/Seeds	|
|	/article/admin/Topics/{id}	|	{version}/article/admin/Topics/{id}	|
|	/article/admin/Topics	|	{version}/article/admin/Topics	|
|	/article/admin/Votes/{id}	|	{version}/article/admin/Votes/{id}	|
|	/article/admin/Votes	|	{version}/article/admin/Votes	|
|	/article/admin/votes/Option/{id}	|	{version}/article/admin/votes/Option/{id}	|
|	/article/admin/votes/Option	|	{version}/article/admin/votes/Option	|
|	/article/admin/WordDictionary/{id}	|	{version}/article/admin/WordDictionary/{id}	|
|	/article/admin/WordDictionary	|	{version}/article/admin/WordDictionary	|

## 抽奖微服务 /reward

|	原 API	|	新 API	|
|	 -----	|	 -----	|
|	/reward/admin/categories/{id}	|	{version}/reward/admin/categories/{id}	|
|	/reward/admin/categories	|	{version}/reward/admin/categories	|
|	/reward/admin/goods/{id}	|	{version}/reward/admin/goods/{id}	|
|	/reward/admin/goods	|	{version}/reward/admin/goods	|
|	/reward/admin/images/{id}	|	{version}/reward/admin/images/{id}	|
|	/reward/admin/images	|	{version}/reward/admin/images	|
|	/reward/admin/notices/{id}	|	{version}/reward/admin/notices/{id}	|
|	/reward/admin/notices	|	{version}/reward/admin/notices	|
|	/reward/admin/prizes/{id}	|	{version}/reward/admin/prizes/{id}	|
|	/reward/admin/prizes	|	{version}/reward/admin/prizes	|
|	/reward/admin/records/{id}	|	{version}/reward/admin/records/{id}	|
|	/reward/admin/records	|	{version}/reward/admin/records	|
|	/reward/admin/shares/{id}	|	{version}/reward/admin/shares/{id}	|
|	/reward/admin/shares	|	{version}/reward/admin/shares	|

## 抽奖微服务 /award

|	原 API	|	新 API	|
|	 -----	|	 -----	|
|	/award/records/{id}	|	{version}/award/records/{id}	|
|	/award/notices	|	{version}/award/notices	|
|	/award/shares/{id}	|	{version}/award/shares/{id}	|
|	/award/prizes	|	{version}/award/prizes	|
|	/award/notices/{id}	|	{version}/award/notices/{id}	|
|	/award/shares	|	{version}/award/shares	|
|	/award/categorys	|	{version}/award/categorys	|
|	/award/user/lucks	|	{version}/award/user/lucks	|
|	/award/records	|	{version}/award/records	|
|	/award/user/prizes	|	{version}/award/user/prizes	|
|	/award/prizes/{id}	|	{version}/award/prizes/{id}	|
|	/award/user/shares	|	{version}/award/user/shares	|

