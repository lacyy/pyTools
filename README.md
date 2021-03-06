# pyTools
琐碎的python工具集，仅供娱乐

哦，代码都是搜刮来的，在from中有原网址> <

---

## ip_scaner.py

说明：扫描局域网中所有存活主机（依据ping）

用法： ```python ip_scaner.py 192.168.172.15```

资料： TTL（生存时间值）表示ping的过程中一过经过了多少个路由器，但它的数据并不是直接给出的。其工作原理是为了防止由于路由器的设置错误，使一些数据包在两个路由器之间来回传送。因为当TTL为0的时候，数据句会丢失，这样当出现循环时候，总有一个时间会使TTL为0从而使数据包丢弃。

总结：确定存活主机，使用ping命令，以返回信息中是否存在TTL字段为判断条件（不存在TTL字段返回-1）。

---

## portscanner.py

说明：扫描某一IP的所有可用端口

用法：```python portscanner.py  192.168.172.15```

资料：在python的socket中SOCK_STREAM（TCP连接），SOCK_DGRAM（UDP连接）

总结：使用TCP连接，以是否连接超时为判断条件。

---

## check_ip138.py

说明：检查IP或域名归属地

用法：```python check_ip138.py www.baidu.com```或者```python check_ip138.py 115.239.211.112```

资料：```def DO(domain)```中正则，源代码中为```r=re.compile(r'&gt; (.*)<br/><b>查询结果：(.*)</b><br/>')```这里的```(.*)```是不包括换行符的任意字符。大概由于时间久远，网页发生了改变，返回的数据中含有换行符，所以一直无法匹配。如果要匹配包含的换行符的任意字符，可以使用```([\s\S]*)```

总结：以urllib2库为基础，通过ip138的接口查询，分析返回的数据信息，提取所需要的结果。


---

## scanner_allip_with_port.py

说明: 扫描局域网中指定端口(默认80)开放的所有IP

用法: ```python scanner_allip_with_port.py 192.168.123.2 8089``` 或者 ```python scanner_allip_with_port.py 192.168.123.2```

资料: 参考ip_scaner.py和portscanner.py

