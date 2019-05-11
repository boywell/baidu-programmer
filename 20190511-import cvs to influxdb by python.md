title: 通过python导入cvs数据到influxdb

date: 2019-05-11 22:40:14



# 导入cvs文件到influxdb-python方式

## 使用工具
```
https://github.com/fabio-miranda/csv-to-influxdb
```

## 工具简介

实用起来很简单，而且作者也在readme中详细的罗列了入参，并写了一个示例。

使用时，如果没有安装python_influxdb的话可能会报错，那么，你需要先安装下python_influxdb

访问地址：https://github.com/influxdata/influxdb-python，在README中详细了介绍如何使用。

使用pip安装方式：

```
pip install influxdb
```

安装完成后就可以愉快的玩耍了。

### 常用命令解释

-s：表示influxdb服务器信息，默认为：localhost:8086

-u：influxdb数据库用户名

-p：influxdb数据库密码

--dbname：influxdb数据库名

-m：表示要插入的数据的表名

--fieldcolumns：字段，多个使用逗号隔开

--tagcolumns：tag，多个使用逗号隔开

-tc：表示时间字段名称：默认为timestamp

-tf：对时间格式化类型，默认为'%Y-%m-%d %H:%M:%S'，注意，使用时格式为：-tf "%Y-%m-%d %H:%M:%S"

## 示例

```shell
python csv-to-influxdb.py -s 127.0.0.1:8086 -u telegraf -p telegraf --dbname telegraf -tf "%Y/%m/%d %H:%M:%S" -tc time -m cpu --input 1.csv --tagcolumns host --fieldcolumns cpu_usage
```

