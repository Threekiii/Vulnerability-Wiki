# Coremail论客邮件系统路径遍历与文件上传漏洞

监测到Coremail论客邮件系统存在路径遍历与文件上传漏洞，攻击者可利用/lunkr/cache/;/;/../../manager/html 设置参数X-Forwarded-For: 127.0.0.1.Coremail 的 nginx 配置文件中，未针对/lunkr/cache 路径向上解析的时候做 X-Forwarded-For 字段的限制，从而可以利用该接口实现配合利用 nginx 不解析，但 tomcat 解析的差异特性，实现绕过 tomcat manager 的本地 ip 限制。

情报见：https://forum.ywhack.com/viewthread.php?tid=115403

通过/lunkr/cache/;/;/../../manager/html进入Tomcat控制台，部署war包进行getshell。

![-w716](media/16215868078702/16215868539351.jpg)

https://forum.ywhack.com/thread-115484-1-5.html