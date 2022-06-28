# Php is easy
* Link: `103.245.249.76:49154`
* Click và link thì đập ngay vào mắt chúng ta là source code của web. 
``` php
<?php
require "flag.php";
error_reporting(0);
 $md51 = md5( '0gdVIdSQL8Cm' ); 
 $a = @$_GET[ '0ni0n' ]; 
 $md52 = @md5($a); 
 if ( isset ($a)){ 
    if ($a != '0gdVIdSQL8Cm' && $md51 == $md52) { 
        echo "<script>alert('$flag')</script>"; 
    } else { 
        echo "0ni0n{F3k4_Fl4G}"; 
    } 
} 
show_source(__FILE__);
?>
```
* Lướt nhanh qua thì có vài điều đáng chú ý ở trong đoạn code này là chúng ta sẽ phải truyền tham số “a” vào để có thể bypass vào các dòng if. Vulnerable ở đây tên là “type juggling” nghĩa là php sẽ không cần ta khai báo kiểu dữ liệu mà sẽ tự động convert sang dạng common và có thể so sánh được với các kiểu dữ liệu khác. Trong source code sử dụng đoạn loose comparison như sau:
`($a != '0gdVIdSQL8Cm' && $md51 == $md52)`
* Nghĩa là sẽ chỉ so sánh giá trị của biến mà không quan tâm đến kiểu dữ liệu hiện tại của biến nên attacker có thể gán giá trị cho biến input $1(khác kiểu dữ liệu so với biến khác)  cùng giá trị với biến dùng để so sánh. Và thêm 1 điều nữa là đối với các mã hash MD5 trong php có format “0e”number from 0 to 9””(ví dụ như 0e366928091944678781059722345471), khi so sánh php sẽ hiểu là các mã hash đó có giá trị bằng nhau nên payload cho challenge này sẽ là:
`http://103.245.249.76:49154/?0ni0n=0e1137126905/`
* trong đó giá trị của 0ni0n là các đoạn kí tự mà khi chuyển dang md5 sẽ có format “0e”numberFrom0To9””

### Flag: FPTUHACKING{Md5_bY_pAAs_eZ_H4_H4}
