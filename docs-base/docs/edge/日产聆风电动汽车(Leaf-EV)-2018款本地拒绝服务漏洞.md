# 日产聆风电动汽车(Leaf EV) 2018款本地拒绝服务漏洞


日产聆风电动汽车（EV）的主机显示屏本地拒绝服务漏洞，可用于锁定屏幕。锁定后，汽车仍可行驶，但无法再使用显示器（即使汽车已关闭或打开）。解锁屏幕的唯一方法是卸下并重新插入包含映射数据的SD卡。

复现步骤：

* 1.要测试的汽车需要与Nissan移动应用程序配对，并启用NissanConnect订阅。
* 2.打开汽车，通过检查SOS按钮上的小灯亮起，验证具有SOS功能的NissanConnect是否已启用。
* 3.按SOS按钮触发紧急呼叫。
* 4.在关闭汽车的同时，立即按住SOS按钮取消通话。
* 5.SOS呼叫将锁定主机，并一直保持这种状态，直到SD卡被取出并重新插入后才重新启动显示面板。

ref:

https://wwws.nightwatchcybersecurity.com/2021/03/14/local-denial-of-service-in-nissan-leaf-ev-2018-head-unit-display/