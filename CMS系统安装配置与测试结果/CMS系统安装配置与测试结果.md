一、下载CMS系统Drupal  
1. 访问Drupal网站，下载最新版本8.9.0-beta2.zip文件。  
https://github.com/drupal/drupal/releases  
2. 创建文件夹C:\xampp\htdocs\d8，将上述文件解压至此文件夹。  
3. 下载汉化包drupal-8.9.0-beta2.zh-hans.po文件。  
http://ftp.drupal.org/files/translations/8.x/drupal/drupal-8.0.0-beta12.zh-hans.po  
4. 在C:\xampp\htdocs\d8\sites\default目录下创建files文件夹，在files目录下创建translations文件夹，将汉化包文件移动至此文件夹。  
5. 将C:\xampp\htdocs\d8\sites\default目录下的default.settings.php文件复制一份，命名为settings.php。  
6. 访问http://localhost/d8/ ，网页报错。  
  
参考资料：https://www.zhi12.cn/node/8901
  
二、安装php管理工具composer  
7. 访问composer网站，下载Composer-Setup.exe文件。  
https://getcomposer.org/download/  
8. 安装composer，注意php.exe文件的位置是C:\xampp\php。  
9. 打开cmd，使用composer命令验证是否安装成功。  
10. 使用composer install命令下载和安装资源。  
![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/CMS系统安装配置与测试结果/composer1.PNG)  
![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/CMS系统安装配置与测试结果/composer2.PNG)  
![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/CMS系统安装配置与测试结果/composer3.PNG)  
  
参考资料：https://blog.csdn.net/m0_37888039/article/details/90071138?ops_request_misc=&request_id=&biz_id=102&utm_source=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4  
  
三、启用php缓存工具opcache  
11. 打开C:\xampp\php\php.ini，搜索opcache，在[opcache]下面添加以下代码：  
```
zend_extension=D:/www/php/ext/php_opcache.dll
opcache.memory_consumption=128
opcache.interned_strings_buffer=8
opcache.max_accelerated_files=4000
opcache.revalidate_freq=60
opcache.fast_shutdown=1
opcache.enable_cli=1
```
  
参考资料：https://blog.csdn.net/longzhoufeng/article/details/70666399  
  
四、设置响应时间  
12. 打开C:\xampp\php\php.ini，搜索max_execution_time，将max_execution_time = 30改为max_execution_time = 300，重启apache。  
  
参考资料：https://blog.csdn.net/u011650048/article/details/42213691?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522158806113019195162541268%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.57650%2522%257D&request_id=158806113019195162541268&biz_id=0&utm_source=distribute.pc_search_result.none-task-blog-2~all~first_rank_v2~rank_v25-1  
  
五、安装CMS系统Drupal  
13. 访问http://localhost/d8/ ，选择语言。  
![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/CMS系统安装配置与测试结果/选择语言.PNG)   
14. 选择安装方式。  
![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/CMS系统安装配置与测试结果/选择安装方式.PNG)  
15. 检查安装需求，如已启用opcache，则这一步自动跳过。  
![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/CMS系统安装配置与测试结果/检查安装需求.PNG)    
16. 设置数据库。  
![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/CMS系统安装配置与测试结果/设置数据库.PNG)  
17. 安装网站。  
![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/CMS系统安装配置与测试结果/安装网站.PNG)  
18. 安装翻译。  
![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/CMS系统安装配置与测试结果/安装翻译.PNG)   
19. 设置网站。  
![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/CMS系统安装配置与测试结果/设置网站.PNG)  
20. 完成翻译。  
![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/CMS系统安装配置与测试结果/完成翻译.PNG)  
21. 简单测试。  
![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/CMS系统安装配置与测试结果/简单测试.PNG)  
  
参考资料：http://drupalchina.cn/node/5530
