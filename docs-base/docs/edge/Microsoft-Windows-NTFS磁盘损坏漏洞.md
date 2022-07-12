# Microsoft Windows NTFS磁盘损坏漏洞

以某种方式尝试访问文件夹中的$i30 NTFS属性，驱动器可能会损坏。攻击者可利用该漏洞，构造恶意命令隐藏在Windows快捷方式文件，批处理文件等方式传递来触发漏洞，导致文件系统索引损坏的硬盘错误。

PoC：


```
“cd c:\:$i30:$bitmap”
```

ref：

http://forum.ywhack.com/redirect.php?goto=findpost&ptid=114994&pid=115409

https://mp.weixin.qq.com/s/kieR-mJ09LoGBYrCMTcpRA