# Challenge
```php 
<?php
show_source(__FILE__);
$flag = "xxxx";
if(isset($_GET['time'])){ 
        if(!is_numeric($_GET['time'])){ 
                echo 'The time must be number.'; 
        }else if($_GET['time'] < 60 * 60 * 24 * 30 * 2){ 
                        echo 'This time is too short.'; 
        }else if($_GET['time'] > 60 * 60 * 24 * 30 * 3){ 
                        echo 'This time is too long.'; 
        }else{ 
                sleep((int)$_GET['time']); 
                echo $flag; 
        } 
                echo '<hr>'; 
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