# 微信授权登录 - 学习笔记

## 1. 登录方式
- 微信开放平台：PC端二维码扫描；
- 微信公众号：手机端弹出微信授权页面；

## 2. 实现方式
- 没有自己的账号体系：直接拉取微信用户信息来进行网站 
- 有自己的账号体系：授权成功后需要绑定自己的账号；需要绑定微信`openid`了；

## 3. OAuth 2.0 协议
### 3.1 简介
- OAuth：Open Authorization 开放式授权协议；
- OAuth：为用户资源的授权提供了一个安全、开放、简易的标准；不会使第三方接触到用户的账号信息；

###3.2 原理
![原理图](./1491916594616.png)

### 3.3 版本
- `OAuth 1.0`：发布于2007年，有较为严重的漏洞；
- `OAuth 2.0`：发布与2010年，被大型企业广泛使用；

### 3.4 场景
- 授权登录；
- 符合授权规则的情况下访问各种API；
- 公司内部的资源开放；

### 3.5 步骤
**步骤一：请求OAuth登录页**
- `Request Token URL` ：未授权的令牌请求地址；未授权时请求带有特定参数的URL；
- `app_id`：每一个唯一的客户端都有一个APP_ID；
- `redirect_uri`：客户端回调地址；

**步骤二：用户使用QQ号登录并授权**
- `redirect_uri`：用户登录成功后会跳转的地址；
- `code`：请求成功后返回的结果；

**步骤三：返回登录结果**
- `User Authorization URL`：用户授权的令牌请求服务地址；授权之后需要请求带有参数的URL；
- `app_id`：客户端账号；
- `app_key`：客户端密码；
- `code`：授权登录后的结果；在规定时间范围内（很短），只可以使用一次的字符串；
- `AccessToken`：用户通过第三方应用访问OAuth接口的令牌；具有较长的生命周期；
- `RefreshToken`：获取新的令牌；