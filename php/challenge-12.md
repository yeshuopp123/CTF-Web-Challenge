# Challenge 
```php 
<?php 

include "flag2.php";
error_reporting(0);
show_source(__FILE__);

$a = @$_REQUEST['hello'];
eval("var_dump($a);"); 
```

# Refference
+ [XNUCA 赛前指导 default](http://218.76.35.74:20131/index2.php)