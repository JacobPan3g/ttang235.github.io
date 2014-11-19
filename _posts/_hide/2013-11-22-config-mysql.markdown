---
layout: post
title: MySQL config file---fixing "MySQL has gone away" problem
categories: config
---
If you get an error message like "MySQL has gone away", maybe the reason is that the default max\_allowed\_packet is not enough for your query. 

Solution 1:

1. execute _SET GLOBAL max\_allowed\_packet=1073741824;_ 

#1 Gigabyte

2. reconnect to sql server

The downside of solution 1 is that when restarting sql server, this setting will be reset to default.

Solution 2:

1. Win+R(shortcut for 'run'), type services.msc, Enter
2. You could find an entry like 'MySQL56', right click on it, select properties
3. You could see sth like "D:/Program Files/MySQL/MySQL Server 5.6/bin\mysqld" --defaults-file="D:\ProgramData\MySQL\MySQL Server 5.6\my.ini" MySQL56

http://bugs.mysql.com/bug.php?id=68516

http://dev.mysql.com/doc/refman/5.0/en/packet-too-large.html

http://stackoverflow.com/a/20136523/1316649

//unfinished.
