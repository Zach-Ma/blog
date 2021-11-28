---
title: "基于OAuth2协议和JWT实现简单的认证和授权系统"
date: 2021-08-27T23:38:23+08:00
draft: true
---

写这个demo的初衷由自心中的SaaS梦，从哪里开始呢，当然是从Auth Server开始。

## API first 

### 授权服务器

授权服务器(authorization server)主要职责是**颁发**和**验证**访问令牌，对此提供两个接口：

- `/token`
- `/verify-token`

通常一个有效的令牌需要和客户端、用户绑定的，授予某用户在某客户端某一时间段内访问资源的权限。

授权服务器需要提供的服务模块应该有：

- `ClientDetailService`:获取客户端信息
- `UserDetailService`:获取用户信息
- `TokenStore`:存储令牌
- `TokenService`:生成及管理令牌，使用TokenStore
- `TokenGrantService`:根据授权类型进行不同的验证流程，以及利用TokenService

## Reference

- [OAuth 2.0的四种方式][1]
  
[1]:https://www.ruanyifeng.com/blog/2019/04/oauth-grant-types.html
