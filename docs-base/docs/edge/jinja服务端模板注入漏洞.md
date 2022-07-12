# jinja服务端模板注入漏洞


程序使用了jinja2的某个渲染函数 比如render_template_string，且存在可控输入点，可造成命令执行漏洞。

详情可以参考这篇文章：https://secure-cookie.io/attacks/ssti/#what-is-template

输入 {{7*7}} 看是否输出 49

利用方式可以参考：https://secure-cookie.io/attacks/ssti/#how-is-that-exploitable
