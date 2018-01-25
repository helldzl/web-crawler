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

{version} = /v1

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


