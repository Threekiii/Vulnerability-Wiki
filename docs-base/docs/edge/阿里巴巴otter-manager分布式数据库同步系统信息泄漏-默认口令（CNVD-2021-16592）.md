# 阿里巴巴otter manager分布式数据库同步系统信息泄漏/默认口令（CNVD-2021-16592）

阿里巴巴otter manager分布式数据库同步系统是基于数据库增量日志解析，准实时同步到本机房或异地机房的mysql/oracle数据库，一个分布式数据库同步系统。阿里巴巴otter manager分布式数据库同步系统存在信息泄露漏洞，攻击者可利用漏洞获取zookper信息。

FOFA：

```
title="Otter Manager"
```

默认口令：admin/admin

进入后直接f12查看元素，修改password为text即可查看数据库等敏感信息密码。

ref：

* https://www.cnvd.org.cn/flaw/show/CNVD-2021-16592
* https://forum.ywhack.com/thread-115309-1-8.html