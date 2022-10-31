# Vulnerability Wiki
**【免责声明】本仓库所涉及的技术、思路和工具仅供学习，任何人不得将其用于非法用途和盈利，否则后果自行承担。**

**【使用说明】**

- 2.0版本重新划分漏洞分区，优化搜索策略
- 全局搜索不支持Wooyun及0sec
- 零组漏洞库请移步左侧导航栏0sec，跳转后通过`ctril+F`进行查找
- 乌云镜像站请移步左侧导航栏Wooyun

**【目录总览】**

- [sidebar](_sidebar.md)

**【最近更新】**

- 2022.10.24
  - webapp/Dogtag PKI XML实体注入漏洞 CVE-2022-2414
  - webapp/Dolibarr edit.php 远程命令执行漏洞 CVE-2022-40871
  - iot/Fortinet FortiOS admin 远程命令执行漏洞 CVE-2022-40684
  
- 2022.10.17
  - webapp/用友 畅捷通远程通 GNRemote.dll SQL注入漏洞
  - webapp/AVEVA InTouch安全网关 AccessAnywhere 任意文件读取漏洞 CVE-2022-23854 
  - webapp/Dapr Dashboard configurations 未授权访问漏洞 CVE-2022-38817
  - appserver/WordPress All-in-One Video Gallery video.php 任意文件读取漏洞 CVE-2022-2633

- 2022.10.11
  - vulhub/Apache APISIX Dashboard API权限绕过导致RCE CVE-2021-45232
- 2022.10.08

  - webpp/GLPI htmLawedTest.php 远程命令执行漏洞 CVE-2022-35914
  
  
    - webapp/Atlassian Bitbucket archive 远程命令执行漏洞 CVE-2022-36804
  
  
  
    - oa/通达OA v11.9 getdata 任意命令执行漏洞
  
  
  
    - oa/泛微OA E-Office OfficeServer.php 任意文件上传漏洞
  
  
  
    - framework/Laravel Filemanager插件 download 任意文件读取漏洞 CVE-2022-40734
  


- 2022.09.13
  - oa/泛微OA E-Cology jqueryFileTree.jsp 目录遍历漏洞
  - oa/万户OA DocumentEdit.jsp SQL注入漏洞
  - oa/万户OA TeleConferenceService XXE注入漏洞
  - oa/万户OA DownloadServlet 任意文件读取漏洞  
  - iot/FLIR-AX8-res.php-后台命令执行漏洞 
  - iot/FLIR-AX8 download.php 任意文件下载
  - os/Linux-openvswitch权限提升漏洞-CVE-2022-2639 
  - webserver/muhttpd 任意文件读取漏洞 CVE-2022-31793
  - webapp/用友 畅捷通T+ Upload.aspx 任意文件上传漏洞
- 2022.09.09
  - webserver/Apache Spark doAs 远程命令执行漏洞 CVE-2022-33891
  - webapp/用友 畅捷通T+ DownloadProxy.aspx 任意文件读取漏洞
  - webapp/漏洞相关用友 畅捷通T+ RecoverPassword.aspx 管理员密码修改漏洞
- 2022.08.29
  - oa/O2OA invoke 后台远程命令执行漏洞 CNVD-2020-18740
  - webapp/Webgrind fileviewer.phtml 任意文件读取漏洞 CVE-2018-12909
  - webapp/Webmin password_change.cgi 远程命令执行漏洞 CVE-2019-15107
  - webapp/Webmin rpc.cgi 后台远程命令执行漏洞 CVE-2019-15642
  - webapp/Webmin update.cgi 后台远程命令执行漏洞 CVE-2022-0824
- 2022.08.24 
  - oa/万户OA OfficeServer.jsp 任意文件上传漏洞
  - oa/泛微OA E-Cology VerifyQuickLogin.jsp 任意管理员登录漏洞
  - oa/用友 GRP-U8 UploadFileData 任意文件上传漏洞
  - oa/致远OA wpsAssistServlet 任意文件上传漏洞
  - oa/致远OA 帆软组件 ReportServer 目录遍历漏洞
  - webapp/NPS auth_key 未授权访问漏洞
  - webapp/Roxy-Wi options.py 远程命令执行漏洞 CVE-2022-31137
  - iot/HIKVISION 综合安防管理平台 applyCT Fastjson远程命令执行漏洞
  - iot/Teleport堡垒机 do-login 任意用户登录漏洞
  - iot/Teleport堡垒机 get-file 后台任意文件读取漏洞
  - iot/安恒 明御WEB应用防火墙 report.php 任意用户登录漏洞
- 2022.07.15 
  - vulhub/Django-Trunc(kind)-and-Extract(lookup_name)-SQL注入漏洞-CVE-2022-34265

- 2022.07.06 
  - appserver/WordPress-Simple-File-List-ee-downloader.php-任意文件读取漏洞-CVE-2022-1119

- 2022.07.05 
  - vulhub/Grafana管理后台SSRF

- 2022.06.23 
  - appserver/WordPress-WP_Query-SQL注入漏洞-CVE-2022-21661
  - os/Linux eBPF权限提升漏洞 CVE-2022-23222

- 2022.06.06 
  - vulhub/Confluence OGNL表达式注入命令执行漏洞-CVE-2022-26134

- 2022.05.17
  -  vulhub/Metabase任意文件读取漏洞-CVE-2021-41277


## 声明

本项目收集漏洞均源于互联网，主要来自以下项目：

- Vulhub：https://github.com/vulhub/vulhub
- Vulhub复现：https://github.com/Threekiii/Vulhub-Reproduce
- Peiqi：https://github.com/PeiQi0/PeiQi-WIKI-Book
- EdgeSecurity： https://github.com/EdgeSecurityTeam/Vulnerability
- 0sec：零组漏洞库。零组已于2021年停运。内容来源于互联网.docx文件，已全部转换为.html文件。
- Wooyun：乌云漏洞库。乌云已于2016年停运，镜像参考 https://github.com/V7hinc/wooyun_final

