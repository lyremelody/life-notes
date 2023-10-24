[返回上层](./README.md)

# SSO

<strong><font color="red">最后修改于2023-09-12</font></strong>

- [SSO](#sso)
  - [1 SSO，Single Sign-On](#1-ssosingle-sign-on)
  - [2 SSO，Single Sign-Off](#2-ssosingle-sign-off)
  - [3 SSO 关注点](#3-sso-关注点)
  - [4 SSO 实现前提](#4-sso-实现前提)
  - [5 SSO 优点](#5-sso-优点)
  - [6 SSO 缺点](#6-sso-缺点)
  - [参考资料](#参考资料)


## 1 SSO，Single Sign-On
SSO (Single sign-on)，单点登录(单一签入)，一种对于许多相互关连，但是又是各自独立的软件系统，提供访问控制的属性。当拥有这项属性时，当用户登录时，就可以获取所有系统的访问权限，不用对每个单一系统都逐一登录。SSO 是一种帮助用户快捷访问网络中多个站点的安全通信技术。

单点登录系统基于一种安全的通信协议，该协议通过多个系统之间的用户身份信息的交换来实现单点登录。使用单点登录系统时，用户只需要登录一次，就可以访问多个系统，不需要记忆多个口令密码。单点登录使用户可以快速访问网络，从而提高工作效率，同时也能帮助提高系统的安全性。

## 2 SSO，Single Sign-Off
同样，单一退出 (Single sign-off)，只需要单一的退出动作，就可以结束对于多个系统的访问权限。

## 3 SSO 关注点
1. 解决用户体验问题
2. 无特定类别的用户
3. 实现一点登录、全局进入，无访问控制能力。

## 4 SSO 实现前提
要实现SSO，需要以下主要功能：
1. **系统共享**：统一的认证系统是SSO的前提之一。认证系统的主要功能是将用户的登录信息和用户信息库相比较，对用户进行登录认证；认证成功后，认证系统应该生成统一的认证标识(ticket)，返还给用户；另外，认证系统还应该对ticket进行校验，判断其有效性。
2. **信息识别**：要实现SSO让用户只登录一次，就必须让应用系统能够识别已经登录过的用户。应用系统应该能对ticket进行识别和提取，通过与认证系统的通讯，能自动判断当前用户是否登录过，从而完成单点登录的功能。

另外：
1. **单一的用户信息数据库并不是必须的**，有许多系统不能将所有的用户信息都集中存储，应该允许用户信息放置在不同的存储中。事实上，只要统一认证系统、统一ticket的生成和校验，无论用户信息存储在什么地方，都能实现单点登录。
2. **统一的认证系统并不是说只有单个的认证服务器**。当用户在访问“应用系统1”时，由第一个认证服务器进行认证后，得到由此服务器产生的ticket。当他访问“应用系统2”时，“认证服务器2”能够识别此ticket是由第一个认证服务器产生的，通过认证服务器之间标准的通讯协议(例如SAML)来交换认证信息，仍然能够完成SSO的功能。

## 5 SSO 优点
SSO为所有其它应用程序和系统，以集中的验证服务器提供身份验证并结合技术，确保用户不必频繁输入密码。

使用单点登录的好处包括：
* 降低访问第三方网站的风险（不存储用户密码，或在外部管理）。
* 减少因不同的用户名和密码组合而带来的密码疲劳。
* 减少为相同的身份重新输入密码所花费的时间。
* 因减少与密码相关的调用IT服务台的次数而降低IT成本。

## 6 SSO 缺点
* 不利于重构：因为涉及的系统很多，要重构必须要兼容所有的系统，可能很耗时。
* 无人看守桌面时有安全风险：因为只需要登录一次，所有的授权的应用系统都可以访问，可能导致一些很重要的信息泄露。

## 参考资料
1. [SSO、4A到IAM 的进化](https://zhuanlan.zhihu.com/p/464185329)
2. [单点登录](https://zh.wikipedia.org/zh-cn/%E5%96%AE%E4%B8%80%E7%99%BB%E5%85%A5)
3. [SSO](https://baike.baidu.com/item/SSO/3451380)
4. [Introduction to Single Sign-On](http://www.opengroup.org/security/sso/sso_intro.htm)