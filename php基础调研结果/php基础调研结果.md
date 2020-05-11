一、试描述PHP程序的运行流程  

PHP语言引擎Zend执行过程如下（不包含Web服务器的执行过程）：  
1.Scanning(Lexing)，将PHP代码转换为语言片段(Tokens)。  
2.Parsing，将Tokens转换成简单而有意义的表达式。  
3.Compilation，将表达式编译成Opocdes。  
4.Execution，顺次执行Opcodes，每次一条，从而实现PHP脚本的功能。  

注：  
PHP代码是在服务器端被执行的。用户访问一个包含PHP代码的网页时，发送Request到服务器，其中包含网页的文件名。服务器收到Request后，找到文件名指向的文件，发现其中嵌有PHP代码，会调用PHP解释器处理该文件，然后将处理后的结果整理到Response，发送到客户端。PHP代码可以与服务器端的数据库或其他资源进行交互，或者根据用户的操作产生不同的页面。  

因此，PHP脚本的触发是在服务器收到客户端的Request。收到一个Request后，服务器触发一个PHP脚本；处理完脚本后，返回结果到客户端，等待下一个Request。当收到下一个Request后，服务器触发另一个（或同一个）PHP脚本。两次PHP脚本的运行是相互独立的，第二次脚本的运行几乎不受前一次脚本运行的影响。  

PHP的代码块PHP代码是可以嵌入到HTML文件中的，经常可以在HTML文件中看到散落在各处的PHP代码块。PHP会忽略两个PHP代码块之间HTML代码。  

>参考资料：  
https://blog.csdn.net/risingsun001/article/details/22888861  
https://blog.csdn.net/fojiedidai/article/details/78611896

二、目前常用的服务器软件有哪些  

Apache是世界使用排名第一的Web服务器软件。它可以运行在几乎所有广泛使用的计算机平台上。Apache源于NCSAhttpd服务器，经过多次修改，成为世界上最流行的Web服务器软件之一。其特点是简单、速度快、性能稳定，并可做代理服务器来使用。  

IIS是微软公司主推的服务器，用户能够利用Windows Server和NTFS（NT File System，NT的文件系统）内置的安全特性，建立强大，灵活而安全的Internet和Intranet站点。  

Tomcat 服务器是一个免费的开放源代码的Web 应用服务器，属于轻量级应用服务器，在中小型系统和并发访问用户不是很多的场合下被普遍使用，是开发和调试JSP 程序的首选。Tomcat是Apache 服务器的扩展，但运行时它是独立运行的，所以当你运行tomcat 时，它实际上作为一个与Apache独立的进程单独运行的。  

>参考资料：  
https://blog.csdn.net/mashuai720/article/details/81205140

三、如何将PHP与Apache建立关联  

1. 配置Apache的httpd.conf文件，使用notepad打开进行编辑。  
查找“Dynamic Shared Object (DSO) Support”的部分，并在最后追加代码：  
```
LoadModule php7_module D:/wamp/php7/php7apache2_4.dll
（该路径为php解压缩后安装后的php7apache2_4.dll文件所在路径）
```
2. 查找“AddType”的部分，并在最后追加代码：
```
AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps
```
3. 查找“DirectoryIndex”的部分，在DirectoryIndex的后面追加一个“index.php”。
4. 在httpd.conf文件里指定PHP配置文件php.ini的目录，这里定位到httpd.conf文件的未尾，在文本最后一行添加如下代码：
```
PHPIniDir "D:/php/php.ini"
（该路径为php.ini文件存放的实际路径）
```
5. 在Apache上配置php文件成功，重启Apache服务。
6. 修改PHP配置文件
将php安装目录下的php.ini-production改名为php.ini  
打开php.ini，做如下修改：  
1） 设置php的扩展路径  
查找 extension_dir = "ext" ，把前面的分号去掉。  
2）开启常用的php扩展，如：  
extension=php_mbstring.dll（php多字节字符串扩展）  
extension=php_mysql.dll（mysql库扩展）  
extension=php_mysql.dll（mysqli库扩展）  
开启方式：查找以上扩展，删掉前面的分号。  
3）设置默认时区  
date.timezone = Asia/Shanghai  
完成所有配置。  

>参考资料：  
https://blog.csdn.net/CWH0908/article/details/82911200


四、主目录下面的子目录和虚拟目录有何不同？

主目录下面的子目录是Web服务器的默认项目路径，将项目放在该路径下，服务器会自动生成配置文件；而虚拟目录不同于主目录下面的子目录，每一个虚拟目录都需要单独配置，才可以进行访问。
