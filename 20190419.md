# 查询List中最大值和最小值
```
  // 最大值
  Collections.max(list);
  // 最小值
  Collections.min(list);

  源码：
    Iterator<? extends T> i = coll.iterator();
    T candidate = i.next();

    while (i.hasNext()) {
        T next = i.next();
        if (next.compareTo(candidate) > 0)
            candidate = next;
    }
    return candidate;

    获取到第一值，作为基准值，然后遍历，如果后续的比这个值大或者小，就把新值赋予基准值，最后得到结果。
```
# influxDB中函数
链接：https://docs.influxdata.com/influxdb/v1.7/query_language/functions



