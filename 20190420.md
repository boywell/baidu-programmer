# Mysql创建用户名并赋权
```
   use mysql;
   create user 用户名 identified by '密码';
   -- 赋权
   grant all privileges on 数据库.* to '用户名'@'%' identified by '密码';
   flush privileges;
```

# Mysql 修改root密码
```
    登录到mysql安装的主机上
    mysqladmin -uroot -p password '新密码'
    输入老密码
```

# 远程登录Mysql主机报错
```
   错误内容：Lost connection to MySQL server at 'reading authorization packet', system error: 0

   在my.cnf中增加以下配置：
   skip-name-resolve=1
   重启mysql
   systemctl restart mysqld
```