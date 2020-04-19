原数数据截图如下：
![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/可编程SQL练习/原始数据.PNG)

执行结果截图如下：
![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/可编程SQL练习/执行结果.PNG)

SQL语句执行过程截图如下：
![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/可编程SQL练习/SQL语句执行过程.PNG)

```
delimiter $$
create procedure delete_five_student(in iid int,out result_s varchar(255))
begin
declare var int default 0;
if iid<2000 then
set result_s = "failure";
else
while var<5 do
delete from t_student where stu_id = iid;
set iid = iid + 1;
set var = var +1;
end while;
set result_s = "success";
end if;
end $$
delimiter ;
set @tar_id = 2000;
set @re = "";
call delete_five_student(@tar_id,@re);
select @re;
set @tar_id = 1999;
set @re = "";
call delete_five_student(@tar_id,@re);
select @re;
```
