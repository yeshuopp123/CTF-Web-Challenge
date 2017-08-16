# Challenge
```php 
<?php
if(isset($_REQUEST[ 'ip' ])) {
    $target = trim($_REQUEST[ 'ip' ]);
    $substitutions = array(
        '&'  => '',
        ';'  => '',
        '|' => '',
        '-'  => '',
        '$'  => '',
        '('  => '',
        ')'  => '',
        '`'  => '',
        '||' => '',
    );
    $target = str_replace( array_keys( $substitutions ), $substitutions, $target );
    $cmd = shell_exec( 'ping  -c 4 ' . $target );
        echo $target;
    echo  "<pre>{$cmd}</pre>";
}
show_source(__FILE__);
```

# Refference 
+ [“春秋杯”web-writeup](https://chybeta.github.io/2017/06/18/%E2%80%9C%E6%98%A5%E7%A7%8B%E6%9D%AF%E2%80%9Dweb-writeup/#WEB-03)