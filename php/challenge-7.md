# Challenge 1
```php 
<?php
if(isset($_POST['reset_username'])) {
		srand(time());
		$token =
		rand(1000000000000000,9999999999999999);
		$success = '<div class="success">Reset password link has been sent to admin@youdontownthisemail.com. Please follow the link ...'
		$hSql->FastQuery('DELETE FROM chal_113 WHERE ip_addr = ?', array($_SERVER['REMOTE_ADDR']));
		$hSql->FastQuery('insert into chal_113 values (?,?,?)', array($_SERVER['REMOTE_ADDR'], $token, time() + 3600));
}
if(URL_HANDLE::GetInstance()->get->k != null) {
		$result = reset($hSql->FastQuery('SELECT * FROM chal_113 WHERE ip_addr = ? AND recovery_key = ? ', array($_SERVER['REMOTE_ADDR'], URL_HANDLE::GetInstance()->get->k)));
		if($hSql->RowCount() != 0) {
				if($result->expired_time > time()) {
						$success = '<div class="success">Here\'s your new password: XXXXXXXXXXXXXX</div>';
				} else {
						$success = '<div class="error">Expired recovery key!</div>';
				}
		} else {
				$success = '<div class="error">Invalid recovery key!</div>';
		}
}
?>
```

# Challenge 2
```
<?php 
$hSql = new MYSQL_HANDLE();
$success = "";
$size = 32;

if(	URL_HANDLE::GetInstance()->post->username == "admin" && 
	URL_HANDLE::GetInstance()->post->password == "XXXXXXXXXXXXXXXX") {

	$success = '<div class="flag">FLAG-XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX</div>';	
} else {
	if(isset($_POST['reset_username'])) {
		$token = "";
		$seed = (int)bin2hex(openssl_random_pseudo_bytes($size / 2));
		srand($seed);
		
		for($i = 0; $i < 16; $i++) {
			$randomDigit = (string)rand() % 10;
			$token .= "," . $randomDigit;
		}
		$token = str_replace(",", "", $token);
		
		$success = '<div class="success">Reset password link has been sent to admin@youdontownthisemailagain.com. Please follow the link http://ringzer0team.com/challenges/120/?k=[your 16 digits code] soon as possible your token expired in 1 hour.</div>';
		$hSql->FastQuery('DELETE FROM chal_120 WHERE ip_addr = ?', array($_SERVER['REMOTE_ADDR']));
		$hSql->FastQuery('INSERT INTO chal_120 VALUES (?,?,?)', array($_SERVER['REMOTE_ADDR'], $token, time() + 3600)); 
	}
	if(URL_HANDLE::GetInstance()->get->k != null) {
		$result = reset($hSql->FastQuery('SELECT * FROM chal_120 WHERE ip_addr = ? AND recovery_key = ? ', array($_SERVER['REMOTE_ADDR'], URL_HANDLE::GetInstance()->get->k)));
		if($hSql->RowCount() != 0) {
			if($result->expired_time > time()) {
				$success = '<div class="success">Here\'s your new password: XXXXXXXXXXXXXXXX</div>';
			} else {
				$success = '<div class="error">Expired recovery key!</div>';
			}
		} else {
			$success = '<div class="error">Invalid recovery key!</div>';
		}
	}
}
?>
```

# Refference 
+ [chybeta : Password reset](https://chybeta.github.io/2017/06/30/%C2%96ringzer0team-web-writeup/#Password-reset)