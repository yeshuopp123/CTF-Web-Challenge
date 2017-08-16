# Challenge
```php
<?php
$a=0;
$b=0;
$c=0;
if (isset($_GET['aaa']))
{
        $aaa = $_GET['aaa'];
		$aaa=="1"?die("Emmm..."):NULL;
        switch ($aaa)
        {
        case 0:
        case 1:
                $a=1;
                break;
        }
}
$bbb=(array)json_decode(@$_GET['bbb']);
if(is_array($bbb)){
    is_numeric(@$bbb["ccc"])?die("Emmm..."):NULL;
    if(@$bbb["ccc"]){
        ($bbb["ccc"]>2017)?$b=1:NULL;
    }
	if(is_array(@$bbb["ddd"])){
        if(count($bbb["ddd"])!==2 OR !is_array($bbb["ddd"][0])) die("Emmm...");
        $eee = array_search("XMAN", $bbb["ddd"]);
        $eee===false?die("Emmm..."):NULL;
        foreach($bbb["ddd"] as $key=>$val){
            $val==="XMAN"?die("Emmm..."):NULL;
        }
        $c=1;
}
}
if($a && $b && $c){
    include "flag.php";
    echo $flag;
}
?>
```

# Solution
```
index.php?aaa=1abcdef&bbb={"ccc":"2018a","ddd":[[1],0]}
```

# Refference
+ [chybeta : PHP](https://chybeta.github.io/2017/07/16/XMAN%E9%80%89%E6%8B%94%E8%B5%9B-2017-web-writeup/#PHP)