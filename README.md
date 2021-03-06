# Factory_Database
SYSU Database Course Project<br>
项目效果请参见Factory_Database/项目展示

## 项目环境
* 编程语言：python3.6<br>
* web框架：python flask<br>
* 数据库：SQL Server<br>
* 操作系统：Windows 10

## 运行方式
Clone后在当前目录下执行命令
```
> python run.py
```
注：运行前需要修改Factory_Database/app/sql.py下的IP地址和SQL Server相关信息

## 摘要
在本次数据库web应用项目中，出于更好、更方便的管理工厂的目的，我所选择的是制作一个工厂管理系统。
在该工厂管理系统中，出于对系统实现的逻辑性考虑，我依据工厂组成部分间的包含关系，将数据库分为三大模块，
每一模块又由几个部分组成，其中第一大模块是客户商和工厂，第二大模块是仓库和车间，第三大模块是产品、零件和工人。
其次，在使用工厂管理系统方面，我将使用人员分为两种，即开发者和普通用户，开发者具备SQL知识，而普通用户不具备SQL知识，
在该数据库应用中，开发者能够使用SQL语言直接对数据库中的表进行修改和更新，而普通用户能够在不具备SQL知识的情况下完成
工厂的基本事务，如生产零件、加工产品、查看工厂情况等等。我依照以上的设计思路，基于**SQL Server**、**python**的**flask**框架，
成功完成了工厂管理系统，并使用**HTML**语言制作成了web应用。

## 工厂管理系统简介
几家工厂需要建立一个管理数据库存储以下信息。<br>
1. 一个工厂由工厂内的多个仓库和工厂内的多个车间组成，并且一个工厂有多个客户商，每个仓库和车间只能属于一个工厂。<br>
2. 一个工厂包含的信息有工厂名、厂长姓名、厂长电话、工厂地址、工厂客户商家名。<br>
3. 一个客户商包含的信息有客户商家名、商家地址，一个客户商可以是多个工厂的客户，一个工厂也可以有多个客户商家。<br>
4. 一个仓库存放了多个零件和多个产品，相同的零件和产品也能够存放到不同的仓库中。<br>
5. 一个仓库包含的信息有仓库号、仓库主任姓名、主任电话、所属工厂名。<br>
6. 一个车间里有许多个工人，每个工人只能属于一个车间，车间里的工人能够制作出许多零件，相同的零件能够由不同的车间和不同的工人制造出来，在零件的制作过程中需要记录制作时间。<br>
7. 一个零件包含的信息有零件号、重量、价格、所属仓库号和被被哪个车间所生产。<br>
8. 一个产品包含的信息有产品号、类别、价格、所属仓库号，一个产品由多个零件所装配而来，一个产品可以由不同的零件组装，一个零件也可以组装多个不同的产品，在产品的组装过程中需要记录组装时间。<br>

## 数据模块介绍
依据实体间的包含关系，数据库分为三大模块：高层模块、中层模块、低层模块。<br>
高层模块：工厂、客户商。<br>
中层模块：仓库、车间。<br>
低层模块：产品、零件、工人。<br>
<div align=center>
<img src="https://github.com/dengzx7/Factory_Database/blob/master/images/%E5%B7%A5%E5%8E%82%E5%AE%9E%E4%BD%93%E6%9E%84%E6%88%90.jpg" width="350">
</div>
<br>
使用工厂管理系统的人分为两类，即开发者和普通用户，开发者有管理员的作用。<br><br>
<div align=center>
<img src="https://github.com/dengzx7/Factory_Database/blob/master/images/%E4%BD%BF%E7%94%A8%E4%BA%BA%E5%91%98%E6%9E%84%E6%88%90.jpg" width="350">
</div>

## 功能介绍
对于开发者，开发者对数据库操作前需要注册个人信息，登陆时需要对照个人信息。开发者能够直接使用SQL语言来操作数据库，能够查询数据库的任意一个表的所有数据或指定属性的数据。开发者能够对数据库的任意表添加满足约束的数据元组。开发者能够对数据库的任意表删除满足约束的数据元组，能够删除一整个表，能够注销用户账号。<br>
<br>
对于普通用户，用户对数据库操作前需要注册个人信息，登陆时需要对照个人信息。用户不需要具备SQL的知识便能够操作数据库。用户能够查询数据库的任意一个表的所有数据或指定属性的数据。用户能够指令车间来生产新的零件。用户能够将新产生的零件存放到仓库中。用户能够通过组装零件来得到新的产品。用户能够将新产生的产品存放到仓库中。用户能够查看各个工厂的工人人数、仓库数量、车间数量、零件数量、产品数量等统计信息，从而评估工厂状况。<br>
<div align=center>
<img src="https://github.com/dengzx7/Factory_Database/blob/master/images/%E6%95%B0%E6%8D%AE%E5%BA%93%E7%B3%BB%E7%BB%9F%E5%8A%9F%E8%83%BD%E6%A6%82%E8%A7%88.jpg" width="400">
</div>

## 开发者模式功能
1. 开发者能够使用SQL语句来操作数据库。
2. 开发者对数据库操作时需要注册个人信息，登陆时需要对照个人信息。
3. 开发者能够查询数据库的任意一个表的所有数据或指定属性的数据。
4. 开发者能够对数据库的任意表添加满足约束的数据元组。
5. 开发者能够对数据库的任意表删除满足约束的数据元组。
6. 开发者能够删除一整个表。
7. 开发者能够注销用户账号。
<br>
<div align=center>
<img src="https://github.com/dengzx7/Factory_Database/blob/master/images/%E5%BC%80%E5%8F%91%E8%80%85%E6%A8%A1%E5%BC%8F%E6%B5%81%E7%A8%8B.jpg" width="500">
</div>

## 普通用户模式功能
1. 用户不需要具备SQL的知识便能够操作数据库。
2. 用户对数据库操作前需要注册个人信息，登陆时需要对照个人信息。
3. 用户能够查询数据库的任意一个表的所有数据或指定属性的数据。
4. 用户能够指令车间来生产新的零件。
5. 用户能够将新产生的零件存放到仓库中。
6. 用户能够通过组装零件来得到新的产品。
7. 用户能够将新产生的产品存放到仓库中。
8. 用户能够查看各个工厂的工人人数、仓库数量、车间数量、零件数量、产品数量等统计信息，从而评估工厂状况。
<br>
<div align=center>
<img src="https://github.com/dengzx7/Factory_Database/blob/master/images/%E6%99%AE%E9%80%9A%E7%94%A8%E6%88%B7%E6%A8%A1%E5%BC%8F%E6%B5%81%E7%A8%8B.jpg" width="550">
</div>

## 数据库功能设计
根据前部分做出的分析，可以得到如下数据库整体功能。
<br>
<div align=center>
<img src="https://github.com/dengzx7/Factory_Database/blob/master/images/%E5%B7%A5%E5%8E%82%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F%E5%8A%9F%E8%83%BD%E8%AE%BE%E8%AE%A1.jpg" width="400">
</div>

## 数据库E-R模型设计
由于各个实体属性较多，所以在ER图中没有显示出属性。在ER图中需要注意的是，工厂与仓库是一对多的关系，工厂与车间是一对多的关系，车间与工人是一对多的关系，除这些外都是多对多的关系。对于联系“制作”和联系“装配”，需要对它们添加属性“日期”来记录装配和制造的日期。
<br>
<div align=center>
<img src="https://github.com/dengzx7/Factory_Database/blob/master/images/%E6%95%B0%E6%8D%AE%E5%BA%93%E7%B3%BB%E7%BB%9FER%E5%9B%BE.jpg" width="700">
</div>

## web应用实现
数据库前端实现思路如下。
<br>
<div align=center>
<img src="https://github.com/dengzx7/Factory_Database/blob/master/images/web%E5%BA%94%E7%94%A8%E5%AE%9E%E7%8E%B0%E6%AD%A5%E9%AA%A4.jpg" width="300">
</div>

## 开发者模式实现
开发者模式设计概览。
<br>
<div align=center>
<img src="https://github.com/dengzx7/Factory_Database/blob/master/images/%E5%BC%80%E5%8F%91%E8%80%85%E6%A8%A1%E5%BC%8F%E6%B5%81%E7%A8%8B.jpg" width="500">
</div>

## 用户模式实现
用户模式设计概览。
<br>
<div align=center>
<img src="https://github.com/dengzx7/Factory_Database/blob/master/images/%E7%94%A8%E6%88%B7%E6%A8%A1%E5%BC%8F%E8%AE%BE%E8%AE%A1%E6%A6%82%E8%A7%88.jpg" width="500">
</div>

