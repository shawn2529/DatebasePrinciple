#### 一、PHP中提供了哪些内置数组，各代表什么意思？自己编码实验

| 数组 | 作用 |
| :-----| :----- |
|$_GET|经由URL请求提交至脚本的变量|
|$_POST|经由HTTP POST方法提交至脚本的变量|
|$_SERVER|变量由web服务器设定或者直接与当前脚本的执行环境相关联|
|$_SESSION|当前注册给脚本会话的变量|
|$_COOKIE|经由HTTP Cookies 方法提交至脚本的变量|
|$_FILES|经由HTTP POST 文件上传而提交至脚本的变量|
|$_ENV|执行环境提交至脚本的变量|
|$_REQUEST|经由GET，POST 和 COOKIE机制提交至脚本的变量（不建议使用）|
|$GLOBALS|包含一个引用指向每个当前脚本的全局范围内有效的变量，该数组的键名为全局变量的名称|

上传页面代码如下：
```
<html>
<head>
<meta charset="utf-8">
<title>PHP内置数组练习</title>
</head>
<body>

<form action="result.php" method="post" enctype="multipart/form-data">
名字：<input type="text" name="fname"><br>
年龄：<input type="text" name="age"><br>
文件：<input type="file" name="file" id="file"><br>
<input type="submit" value="提交">
</form>

</body>
</html>
```

结果页面代码如下：
```
欢迎<?php echo $_POST["fname"]; ?>！<br>
你的年龄是<?php echo $_POST["age"]; ?>岁。<br>
你上传的文件是<?php echo $_FILES["file"]["name"]; ?>。
```

测试结果如下：  
![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/php内置数组练习/测试结果1.PNG)  

![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/php内置数组练习/测试结果2.PNG)  

#### 二、PHP中实现网页间数据传递，可以使用哪几种方法？自己编码实验
##### 1. $\_POST传值  
$\_POST传值是用于html的\<form>表单跳转的方法，例如：  
```
<html>
<form action='跳转页面url路径' method='$_POST'>
<input type='text' name='name1'>
<input type='hidden' name='name2' value='value'>
<input type='submit' value='提交'>
</form>
</html>
```

form表单中的提交按钮按下后，就会把form中有name的内容都传到填入的url中，之后可以通过$\_POST['name']获取内容。  

测试代码如下：  
```
<?php
$a=$_POST['name1'];
$b=$_POST['name2'];
?>
```

##### 2. $\_GET传值  
$\_GET传值是通过跟随url传递的，在页面跳转时，跟着url跳转。常用于\<a>标签的使用。  

测试代码如下：  
```
<a href='delete.php?id=value'>点我跳转</a>
```

跳转进入xxx.php后，就能通过$\_GET['id']获取传递的值。GET方法常用于url的目的是删除或读取某个id的php文件。

##### 3. $\_SESSION传值  
$\_SESSION是全局变量的一种，经常用于用户登陆后保存用户id之类的常用数据。一旦保存到SESSION中，其他页面都可以通过SESSION获取，SESSION的使用要开启session。  

测试代码如下：
```
<?php
//session赋值
   session_start();
   $_SESSION['one']=value1;
   $_SESSION['two']=value2;

//session值的读取:
   $one = $_SESSION['one'];

   //session值的销毁
   unset($_SESSION['one']);
?>
```

>参考资料：https://blog.csdn.net/u010865136/article/details/43667757

#### 三、PHP中Cookie和Session都可以实现用户登陆，他们有什么区别？自己编码实验（不能照抄课件代码）
##### 1. Cookie实现用户登录

登录页面代码如下：
```<?php
if (isset($_POST["username"])){
    $name = $_POST["username"];
    if($name=="xiaozhang" || $name=="xiaoli"){
        $expire=time()+60*60*24*30;
        setcookie("username", "xiaozhang", $expire);
        echo "<script language=javascript>alert('登陆成功！');location.href='cookie_login_success.php';</script>";
    }else{
        echo "<script language=javascript>alert('登陆失败！');</script>";
    }
}

?>
<html>
<form action="cookie_login.php" method="post">
    <input type ="text" name="username">
    <input type ="password" name="password" value="value">
    <input type ="submit" value="提交">
</form>
</html>
```

登陆成功页面代码如下：
```
<?php
echo  "亲爱的".$_COOKIE["username"]."，您已登陆。";
?>
```

测试结果如下：  
![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/php内置数组练习/cookie登录页面.PNG)  

![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/php内置数组练习/cookie登陆成功页面.PNG)  

##### 2. Session实现用户登录

登录页面代码如下：
```
<?php
if (isset($_POST["username"])){
    $name = $_POST["username"];
    if($name=="xiaozhang" || $name=="xiaoli"){
        session_start();
        $_SESSION['username']=$name;
        echo "<script language=javascript>alert('登陆成功！');location.href='session_login_success.php';</script>";
    }else{
        echo "<script language=javascript>alert('登陆失败！');</script>";
    }
}

?>
<html>
<form action="cookie_login.php" method="post">
    <input type ="text" name="username">
    <input type ="password" name="password" value="value">
    <input type ="submit" value="提交">
</form>
</html>
```

登陆成功页面代码如下：
```
<?php
session_start();
echo  "亲爱的".$_SESSION["username"]."，您已登陆。";
?>
```

测试结果如下：  
![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/php内置数组练习/session登录页面.PNG)  

![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/php内置数组练习/session登陆成功页面.PNG)  

#### 四、PHP中我们可以通过内置数组获取哪些服务器信息，如何获取？自己编码实验

测试代码如下：
```
<?php
echo "获取系统类型及版本号：".  php_uname();
echo "<br>";
echo "只获取系统类型：". php_uname('s');
echo "<br>";
echo "只获取系统版本号：". php_uname('r');
echo "<br>";
echo "获取PHP运行方式：".  php_sapi_name() ;
echo "<br>";
echo "获取前进程用户名：". Get_Current_User();
echo "<br>";
echo "获取PHP版本：". PHP_VERSION;
echo "<br>";
echo "获取Zend版本：". Zend_Version();
echo "<br>";
echo "获取PHP安装路径：". DEFAULT_INCLUDE_PATH;
echo "<br>";
echo "获取当前文件绝对路径：".__FILE__;
echo "<br>";
echo "获取Http请求中Host值：". $_SERVER["HTTP_HOST"];
echo "<br>";
echo "获取服务器IP：".  GetHostByName($_SERVER['SERVER_NAME']);
echo "<br>";
echo "接受请求的服务器IP：".  $_SERVER["SERVER_ADDR"];
echo "<br>";
echo "有时候获取不到，推荐用：". GetHostByName($_SERVER['SERVER_NAME']);
echo "<br>";
echo "获取客户端IP：". $_SERVER['REMOTE_ADDR'];
echo "<br>";
echo "获取服务器解译引擎：". $_SERVER['SERVER_SOFTWARE'];
echo "<br>";
echo "获取服务器系统目录：". $_SERVER['SystemRoot'];
echo "<br>";
echo "获取服务器域名：". $_SERVER['SERVER_NAME'];
echo "<br>";
echo "建议使用：". $_SERVER["HTTP_HOST"];
echo "<br>";
echo "获取服务器语言：". $_SERVER['HTTP_ACCEPT_LANGUAGE'];
echo "<br>";
echo "获取服务器Web端口：".  $_SERVER['SERVER_PORT'];
?>
```

测试结果如下：  

![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/php内置数组练习/服务器信息.PNG)  

>参考资料：https://blog.csdn.net/living_ren/article/details/78974898
