#### 题目一  
#### 完成Apache/Nginx + MySQL + PHP基础开发环境的准备工作  

apache使用集成环境xampp的默认配置，将项目新建至C:\xampp\htdocs文件夹。  
![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/php开发调试准备/项目代码.PNG)

#### 题目二  
#### 完成PHP调试工具的安装、配置和使用  

一、安装调试工具Xdebug  
1. 访问Xdebug网站，按照指示输入php信息（使用命令行php -i即可获取信息），下载php_xdebug-2.9.5-7.3-vc15-x86_64.dll文件。  
https://xdebug.org/wizard
2. 将上述文件移动至C:\xampp\php\ext文件夹。
3. 配置php.ini文件，在[opcache]下面做以下修改：
```
zend_extension = C:\xampp\php\ext\php_opcache.dll
```
在文件末尾添加以下代码：
```
[XDebug]
zend_extension = C:\xampp\php\ext\php_xdebug-2.9.5-7.3-vc15-x86_64.dll
xdebug.profiler_output_dir="C:\xampp\out_profile\profiler_output_dir"
xdebug.profiler_enable = On
xdebug.profiler_enable_trigger = off
xdebug.profiler_output_name = cachegrind.out.%t.%p
xdebug.trace_output_dir="C:\xampp\out_profile\trace_output_dir"
xdebug.remote_autostart = 1
xdebug.var_display_max_children=1024
xdebug.var_display_max_data=10240
xdebug.var_display_max_depth=7
xdebug.show_local_vars=0
xdebug.remote_enable = On
xdebug.remote_handler = dbgp
xdebug.remote_host= localhost
xdebug.remote_port = 9000
xdebug.idekey= PHPSTORM
```
4. 在chrome应用商店下载Xdebug helper插件，将IDE设置为PHPStorm。  
![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/php开发调试准备/Xdebug_helper插件设置.PNG)

二、安装调试工具PHPStorm  
1. 访问PHPStorm网站，下载PhpStorm-2020.1.1.exe文件。  
https://www.jetbrains.com/zh-cn/phpstorm/download/download-thanks.html
2. 使用学生邮箱免费激活。  
https://www.jetbrains.com/zh-cn/phpstorm/buy/#discounts?billing=yearly
3. 添加php解释器。  
![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/php开发调试准备/添加php解释器.PNG)
4. 设置Xdebug监听端口。  
![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/php开发调试准备/设置Xdebug监听端口.PNG)
5. 设置DBGp Proxy。  
![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/php开发调试准备/设置DBGp_Proxy.PNG)
6. 设置服务器。  
![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/php开发调试准备/设置服务器.PNG)
7. 设置断点，启动debug模式，测试是否连通。  
![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/php开发调试准备/启动debug模式.PNG)

![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/php开发调试准备/测试结果.PNG)

#### 复习并练习使用编程语言访问数据库，并将运行结果在网页中展现出来  

```
<!DOCTYPE html>
<html lang="zh" dir="ltr">
  <head>
    <meta charset="utf-8">
    <title></title>
  </head>
  <body>
<?php
//连接数据库
$conn = mysqli_connect("localhost","root","shaw2529.+","test",3306);

//判断是否连接成功
if(!$conn){
echo 失败;
}
//选择数据库
mysqli_select_db($conn,"test");

//准备sql语句
$sql = "select * from e1";

//发送sql语句
$obj = mysqli_query($conn,$sql);

echo "<center>";
    echo "<table border = 1 cellspacing = '0' cellpadding = '10'>";
        echo "<th>编号</th><th>姓名</th><th>密码</th>";
        while($row = mysqli_fetch_assoc($obj)){
        echo "<tr>";
            echo '<td>'.$row['a1'].'</td>';
            echo '<td>'.$row['a2'].'</td>';
            echo '<td>'.$row['a3'].'</td>';

            echo "</tr>";
        }

        echo "</table>";
    echo "</center>";

        //关闭连接
        mysqli_close($conn);
        ?>
          </body>
</html>
```
![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/数据库服务端与编程语言连接测试结果/使用php连接MariaDB方法一.PNG)

>参考资料：  
http://www.cnplugins.com/devtool/xdebug-helper/  
https://www.cnblogs.com/baocheng/p/5775938.html  
https://blog.csdn.net/weixin_30745553/article/details/95545875?ops_request_misc=&request_id=&biz_id=102&utm_term=phpstorm%20xdebug%20chrome&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-95545875  
https://blog.csdn.net/qq_32631847/article/details/82054011  

#### 题目三  
#### 安装、调试并使用PHP/Python的一种ORM框架的使用，并编写自己的测试案例与代码  
