学生管理系统初级版
===

## 基本功能介绍

系统提供的功能主要有:

1.学生信息的查询、修改、增加、删除，账户信息的查询、修改、增加、删除

2.登录管理系统的账户分为管理员账户和普通账户，普通用户只具有查询学生信息的功能，管理员用户具有系统提供的所有功能

3.主要用到的数据结构有：链表（内存中存储账号和学生信息），账号和学生信息是一个结构体

## 系统模块设计

### a.登录模块

1.输入用户名和密码，输密码的时候用 * 代表用户输入的内容，输入回车代表结束。

2.当用户输入完用户名和密码后，系统会拿它去跟内存中的用户名和密码匹配，如果匹配成功则进入系统菜单界面、匹配不成功则会直接退出程序。

3.实现方法是采用 #include<conio.h> char c=getch()，getch() 输入时，不会显示在屏幕上，读到一个字符后，就输出一个*。

  当读到的是\b 字符，如何实现退格呢？先输出一个\b,再输出一个空格，再输出一个\b，即使用 printf("\b \b")
  
### b.系统功能菜单显示

当用户选择查询学生信息功能时会根据用户权限的不同显示不同功能的查询功能。

1.当前用户为普通用户时，分为按姓名查询、按学号查询、菜单返回上一层。

2.当前用户为管理员用户时，多了一个查询全部学生信息的功能。

3.系统提供的其他功能只有在管理员权限下才能使用：

菜单2：为添加学生信息。管理员从标准输入输入学生的详细信息，系统会把学生信息按照学号的大小插入到内存的链表中，并同时把链表保存到相应文件中去。(注意:学生的学号是唯一的，如果两学生的学号相同会插入失败)

菜单3：为修改学生的信息。管理员可以根据学号修改学生的其他信息（学号不能修改）。并同时将修改完的信息保存到到文件。

菜单4：为删除学生的信息。管理员可以根据学生的学号删除相应学生的信息。并同时把删除后的学生信息保存到文件中去。

菜单5：是增加账号。所增加的账号名不能与已存在的冲突。增加账号完毕后同时把增加后的信息保存到相应的文件中去。

菜单6：更新账号信息。同时把信息保存到相应文件中去。

菜单7：删除用户账户。管理员根据输入的账户名删除相对应的账户。并把删除后的信息保存到相应的文件中去。

菜单8：查询用户账号信息。

菜单9：退出系统。并同时把信息保存到文件中去。
