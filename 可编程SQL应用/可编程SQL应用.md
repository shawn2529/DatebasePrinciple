SQL语句如下：  
```
create database student;
use student;

create table student(sid int, name varchar(30), year int);
create table all_student(aid int, name varchar(30), year int, status varchar(30));
insert into student values(1,"xiaozhang",2019);
insert into student values(2,"xiaoli",2019);
insert into student values(3,"xiaowang",2019);

insert into all_student values(1,"xiaozhang",2019,"registrated");
insert into all_student values(2,"xiaoli",2019,"registrated");
insert into all_student values(3,"xiaowang",2019,"registrated");

select * from all_student;

delimiter $$
create trigger graduate_2019 after
delete on student
for each row
begin
update all_student set status = "graduated" where year = 2019;
end $$
delimiter ;

delete from student where sid = 1;

select * from all_student;

delimiter $$
create procedure show_graduate_2019()
begin
select * from all_student where status = "graduated"
and year = 2019;
end $$
delimiter ;

call show_graduate_2019;
```
  
创建数据库SQL执行过程截图如下：  
![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/可编程SQL应用/创建数据库.PNG)  
  
创建触发器SQL执行过程截图如下：  
![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/可编程SQL应用/创建触发器.PNG)  
  
创建存储过程SQL执行过程截图如下：  
![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/可编程SQL应用/创建存储过程.PNG)  
