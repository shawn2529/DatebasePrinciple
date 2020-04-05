题目一：  
1. 定义并创建熟人表  
```
DROP TABLE IF EXISTS `accquaintance`;
CREATE TABLE `accquaintance` (
  `friend1` varchar(255) DEFAULT NULL,
  `friend2` varchar(255) DEFAULT NULL,
  `class` varchar(255) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

2. 生成并导入测试数据  
```
INSERT INTO `accquaintance` VALUES ('Sydnee', 'Quyn', 'book');
INSERT INTO `accquaintance` VALUES ('Zahir', 'Callie', 'book');
INSERT INTO `accquaintance` VALUES ('Abel', 'Coby', 'drink');
INSERT INTO `accquaintance` VALUES ('Aphrodite', 'Leonard', 'ball');
INSERT INTO `accquaintance` VALUES ('Macon', 'Channing', 'book');
INSERT INTO `accquaintance` VALUES ('Xerxes', 'Orla', 'ball');
INSERT INTO `accquaintance` VALUES ('Hiroko', 'Emmanuel', 'ball');
INSERT INTO `accquaintance` VALUES ('Yasir', 'Lunea', 'ball');
INSERT INTO `accquaintance` VALUES ('Madonna', 'Dieter', 'book');
INSERT INTO `accquaintance` VALUES ('Griffith', 'Robin', 'drink');
INSERT INTO `accquaintance` VALUES ('Hiram', 'Oscar', 'drink');
INSERT INTO `accquaintance` VALUES ('Teagan', 'Rana', 'ball');
INSERT INTO `accquaintance` VALUES ('Miriam', 'Lana', 'ball');
INSERT INTO `accquaintance` VALUES ('Xander', 'Leroy', 'ball');
INSERT INTO `accquaintance` VALUES ('Lev', 'Wyoming', 'book');
INSERT INTO `accquaintance` VALUES ('Andrew', 'Patrick', 'ball');
INSERT INTO `accquaintance` VALUES ('Veda', 'Arsenio', 'drink');
INSERT INTO `accquaintance` VALUES ('Daryl', 'Yardley', 'drink');
INSERT INTO `accquaintance` VALUES ('Olga', 'Palmer', 'drink');
INSERT INTO `accquaintance` VALUES ('Vladimir', 'Abbot', 'drink');
INSERT INTO `accquaintance` VALUES ('Amery', 'Lev', 'book');
INSERT INTO `accquaintance` VALUES ('Scott', 'Acton', 'book');
INSERT INTO `accquaintance` VALUES ('Tyrone', 'Samson', 'ball');
INSERT INTO `accquaintance` VALUES ('Wayne', 'Maite', 'drink');
INSERT INTO `accquaintance` VALUES ('Kendall', 'Harper', 'ball');
INSERT INTO `accquaintance` VALUES ('Darius', 'Kellie', 'ball');
INSERT INTO `accquaintance` VALUES ('Shaine', 'Lane', 'book');
INSERT INTO `accquaintance` VALUES ('Mason', 'Wylie', 'book');
INSERT INTO `accquaintance` VALUES ('Fitzgerald', 'Kirby', 'drink');
INSERT INTO `accquaintance` VALUES ('Asher', 'Jenette', 'ball');
INSERT INTO `accquaintance` VALUES ('Paul', 'Zorita', 'drink');
INSERT INTO `accquaintance` VALUES ('Fulton', 'Henry', 'book');
INSERT INTO `accquaintance` VALUES ('Dana', 'Bree', 'drink');
INSERT INTO `accquaintance` VALUES ('Merritt', 'Quintessa', 'drink');
INSERT INTO `accquaintance` VALUES ('Michelle', 'Simon', 'book');
INSERT INTO `accquaintance` VALUES ('Kennedy', 'Henry', 'book');
INSERT INTO `accquaintance` VALUES ('Beverly', 'Palmer', 'book');
INSERT INTO `accquaintance` VALUES ('Slade', 'Minerva', 'book');
INSERT INTO `accquaintance` VALUES ('Ronan', 'Neve', 'ball');
INSERT INTO `accquaintance` VALUES ('Hollee', 'Ebony', 'drink');
INSERT INTO `accquaintance` VALUES ('Iris', 'Marvin', 'ball');
INSERT INTO `accquaintance` VALUES ('Lacey', 'Nasim', 'drink');
INSERT INTO `accquaintance` VALUES ('Sydnee', 'Urielle', 'ball');
INSERT INTO `accquaintance` VALUES ('Damon', 'Caldwell', 'ball');
INSERT INTO `accquaintance` VALUES ('Mufutau', 'Kylan', 'ball');
INSERT INTO `accquaintance` VALUES ('Nayda', 'Pascale', 'drink');
INSERT INTO `accquaintance` VALUES ('Eric', 'Cain', 'book');
INSERT INTO `accquaintance` VALUES ('Juliet', 'Hector', 'ball');
INSERT INTO `accquaintance` VALUES ('Asher', 'Quynn', 'ball');
INSERT INTO `accquaintance` VALUES ('Sonya', 'Moses', 'drink');
INSERT INTO `accquaintance` VALUES ('Adrienne', 'Larissa', 'drink');
INSERT INTO `accquaintance` VALUES ('Tashya', 'Austin', 'book');
INSERT INTO `accquaintance` VALUES ('Macaulay', 'Joel', 'ball');
INSERT INTO `accquaintance` VALUES ('Inez', 'Alexa', 'ball');
INSERT INTO `accquaintance` VALUES ('Barclay', 'Nita', 'drink');
INSERT INTO `accquaintance` VALUES ('Gannon', 'Oscar', 'drink');
INSERT INTO `accquaintance` VALUES ('Jemima', 'Zelenia', 'book');
INSERT INTO `accquaintance` VALUES ('Branden', 'Demetrius', 'book');
INSERT INTO `accquaintance` VALUES ('Chadwick', 'Hu', 'book');
INSERT INTO `accquaintance` VALUES ('Hayes', 'Zorita', 'drink');
INSERT INTO `accquaintance` VALUES ('Michael', 'Myra', 'drink');
INSERT INTO `accquaintance` VALUES ('Damon', 'Irene', 'book');
INSERT INTO `accquaintance` VALUES ('Eric', 'Lara', 'book');
INSERT INTO `accquaintance` VALUES ('John', 'Barclay', 'drink');
INSERT INTO `accquaintance` VALUES ('Rigel', 'Joel', 'drink');
INSERT INTO `accquaintance` VALUES ('Hilary', 'Aquila', 'ball');
INSERT INTO `accquaintance` VALUES ('Kyla', 'Thane', 'drink');
INSERT INTO `accquaintance` VALUES ('Channing', 'Matthew', 'drink');
INSERT INTO `accquaintance` VALUES ('Felix', 'Jacob', 'drink');
INSERT INTO `accquaintance` VALUES ('Chanda', 'Maris', 'book');
INSERT INTO `accquaintance` VALUES ('Declan', 'Penelope', 'book');
INSERT INTO `accquaintance` VALUES ('Ciaran', 'Gabriel', 'ball');
INSERT INTO `accquaintance` VALUES ('Riley', 'April', 'book');
INSERT INTO `accquaintance` VALUES ('Lance', 'Xena', 'book');
INSERT INTO `accquaintance` VALUES ('Serena', 'Marsden', 'ball');
INSERT INTO `accquaintance` VALUES ('Vladimir', 'Fredericka', 'drink');
INSERT INTO `accquaintance` VALUES ('Jonas', 'Harlan', 'drink');
INSERT INTO `accquaintance` VALUES ('Acton', 'Chancellor', 'drink');
INSERT INTO `accquaintance` VALUES ('Craig', 'Jin', 'ball');
INSERT INTO `accquaintance` VALUES ('Kibo', 'April', 'book');
INSERT INTO `accquaintance` VALUES ('Gareth', 'Rebekah', 'ball');
INSERT INTO `accquaintance` VALUES ('Ulric', 'Charlotte', 'drink');
INSERT INTO `accquaintance` VALUES ('MacKenzie', 'Rajah', 'ball');
INSERT INTO `accquaintance` VALUES ('Aurelia', 'Lars', 'ball');
INSERT INTO `accquaintance` VALUES ('Odysseus', 'Martena', 'ball');
INSERT INTO `accquaintance` VALUES ('Fallon', 'Kane', 'ball');
INSERT INTO `accquaintance` VALUES ('Mia', 'Medge', 'drink');
INSERT INTO `accquaintance` VALUES ('Maris', 'Sigourney', 'drink');
INSERT INTO `accquaintance` VALUES ('Tamara', 'Hermione', 'ball');
INSERT INTO `accquaintance` VALUES ('Calvin', 'Zeph', 'book');
INSERT INTO `accquaintance` VALUES ('Hasad', 'Moses', 'book');
INSERT INTO `accquaintance` VALUES ('Kevyn', 'Kiara', 'drink');
INSERT INTO `accquaintance` VALUES ('Randall', 'Cherokee', 'ball');
INSERT INTO `accquaintance` VALUES ('Tate', 'Hayes', 'book');
INSERT INTO `accquaintance` VALUES ('Zahir', 'Graham', 'book');
INSERT INTO `accquaintance` VALUES ('Oprah', 'Morgan', 'book');
INSERT INTO `accquaintance` VALUES ('Cameran', 'Samson', 'book');
INSERT INTO `accquaintance` VALUES ('Theodore', 'Dora', 'drink');
INSERT INTO `accquaintance` VALUES ('123', '456', 'drink');
```

题目二：  
1. 找出互不认识的人  
```
with ac as 
(select distinct friend from 
(select friend1 as friend from accquaintance union all select friend2 as friend from accquaintance) a) 
select ac1.friend friend1,ac2.friend friend2 from ac ac1,ac ac2
where ac1.friend != ac2.friend
and not exists(select * from accquaintance where accquaintance.friend1 = ac1.friend and accquaintance.friend2 = ac2.friend) 
and not exists(select * from accquaintance where accquaintance.friend2 = ac1.friend and accquaintance.friend1 = ac2.friend) 
```  
![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/SQL查询课后练习/找出互不认识的人.PNG)  
  
2. 找出只在一个类别里出现的人  
```
with ac as (select friend1 from accquaintance union distinct select friend2 from accquaintance)
select ac.friend1 from ac where (select count(distinct class) from accquaintance where accquaintance.friend1 = ac.friend1 or accquaintance.friend2 = ac.friend1) = 1
```
![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/SQL查询课后练习/找出只在一个类别里出现的人.PNG)  
  
3. 找出所有类别里都有朋友的人  
```
with ac as (select friend1 from accquaintance union distinct select friend2 from  accquaintance)
select ac.friend1 from ac where (select count(distinct class) from accquaintance where accquaintance.friend1 = ac.friend1 or accquaintance.friend2 = ac.friend1) = 3
```
![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/SQL查询课后练习/找出所有类别里都有朋友的人.PNG)  
  
4. 找出每个类别里面朋友最多的人  
```
with ac as 
(select distinct friend from 
(select friend1 as friend from accquaintance union all select friend2 as friend from accquaintance) a),
cl as (select distinct class from accquaintance),
ccc as (select ac1.friend na,count(*) num,CL.class cc from accquaintance,ac ac1,cl 
where (accquaintance.friend1 = ac1.friend or accquaintance.friend2 = ac1.friend) and accquaintance.class = cl.class
 group by CL.class,ac1.friend 
ORDER BY num desc)
select na friend,cc class from ccc group by cc
```
![image](https://github.com/shawn2529/DatebasePrinciple/blob/master/SQL查询课后练习/找出每个类别里面朋友最多的人.PNG)  
  
5. 找出在同一类别里面通过朋友而结识的其他朋友（朋友的朋友也是朋友）  
  
6. 找出这样的人，通过他而结识的朋友对最多(p1和p2原本不相识，他们通过p3结识，那么p3的连接度为1，找出连接度最高的人)  
  
7. 找出臭味相投的朋友，他们在所出现的所有类别里面都是朋友（并且不能有这种情况，其中一个在某个类别里出现而另外一个不出现）  
