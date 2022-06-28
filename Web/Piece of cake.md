# Piece of cake

* Link: `http://103.245.249.76:49155/`
* Source code:
``` php
<?php 
include "flag.php"; 
highlight_file(__FILE__); 
error_reporting(0); 
$str1 = $_GET['0']; 

if(isset($_GET['0'])){ 
    if($str1 == md5($str1)){ 
        echo $onion1; 
    } 
    else{ 
        die(); 
    } 
} 
else{ 
    die();    
} 

$str2 = $_GET['1']; 
$str3 = $_GET['2']; 

if(isset($_GET['1']) && isset($_GET['2'])){ 
    if($str2 !== $str3){ 
        if(hash('md5', $salt . $str2) == hash('md5', $salt . $str3)){ 
            echo $onion2; 
        } 
        else{ 
            die(); 
        } 
    } 
    else{ 
        die(); 
    } 
} 
else{ 
    die();    
} 
?> 
```

* Cũng tương tự như bài “php is easy” nhưng sẽ phải truyền vào 3 tham số thay vì 1 tham số, trong đó tham số 0 sẽ là 1 số có format “0e”number from 0 to 9”” và mã hash của tham số 0 cũng có format như vậy, tham số 1 và 2 thì chỉ cần mã hash md5 có format “0e”number from 0 to 9”” là được
payload: `103.245.249.76:49155/?0=0e215962017&1=240610708&2=QNKCDZO`

### Flag: FPTUHACKING{StR1Ngs_c0nCaTeNaT1oN_1s_EaSy_!!!}
