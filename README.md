# Epay
2020.02彩虹易支付原版开源


### 网站环境需求
PHP版本： >= 7.4

MySQL版本：>= 5.6


### 安装教程
上传源代码到空间或服务器，确保权限可读写。
上传完成后，使用浏览器访问：域名/install/index.php，按步骤流程进行安装。
设置伪静态规则：在目录下有一个Nginx.txt文件，将其复制到伪静态中，不然付款后回调页面会出现404。


伪静态设置：
···
location / {
 if (!-e $request_filename) {
   rewrite ^/(.[a-zA-Z0-9\-\_]+).html$ /index.php?mod=$1 last;
 }
 rewrite ^/pay/(.*)$ /pay.php?s=$1 last;
}
location ^~ /plugins {
  deny all;
}
location ^~ /includes {
  deny all;
}
···
