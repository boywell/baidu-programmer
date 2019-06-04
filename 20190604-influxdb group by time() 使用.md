---
layout: influxdb
title: influxDB group by time使用.md
date: 2019-06-04 18:39:55
tags: influxdb
---




需求：influxdb中同一时间存在多个值，需要对每一秒的数据进行分组，获取到每秒数据总和。

表：test

field : bite

tag：name

按照mysql的思路写的sql：

```mysql
select sum(bite) from test where name='hello' group by time(1s) fill(0) order by time;
```



但是发现一个问题：数据是从name的第一条数据，到当前时间的每一秒的数据。并不是name的开始和结束时间，就像是name筛选未生效，后来发现，group by time(1s) 查询需要指定time的开始和结束时间。所以sql如下：

```mysql
select sum(bite) from test where name='hello' and time >= '2019-06-04T10:01:01Z'
and time <= '2019-06-04T10:11:02Z'
group by time(1s) fill(0) order by time; 
```

time的开始结束值，就是name='hello'的开始和结束值。

概念解释：
time(1s)：表示每一秒做统计

1m：每分钟

1h：每小时

更多含义参见influxdb函数介绍：

[influxdb函数详解从通用函数看时序数据分析方法](https://tanjiti.github.io/2019/02/20/influxdb%E5%87%BD%E6%95%B0%E8%AF%A6%E8%A7%A3/)

[官方1.7版本函数详解](https://docs.influxdata.com/influxdb/v1.7/query_language/functions/)