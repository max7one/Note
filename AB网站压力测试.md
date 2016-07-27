## 安装方式

	sudo apt-get install apache2-utils
	
## 常用命令

	ab -n 1000 http://localhost 
	发起1000次请求 
	
	-n requests 执行的请求数(默认执行一个请求)
	-c concurrency 并发数(同一时间的请求数,默认是1个)
	-k  使用HTTP Keep-Alive特性
	-s  timeout 超时时间(默认30秒)
	-v  详细程度 -4,-3...
	
## 输出信息

	ab -kc 1000 -n 1000 http://localhost 
	//执行1000次并发数为1000的请求

	//输出信息
	This is ApacheBench, Version 2.3 <$Revision: 1706008 $>
	Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
	Licensed to The Apache Software Foundation, http://www.apache.org/

	Benchmarking localhost (be patient)
	Completed 100 requests
	Completed 200 requests
	Completed 300 requests
	Completed 400 requests
	Completed 500 requests
	Completed 600 requests
	Completed 700 requests
	Completed 800 requests
	Completed 900 requests
	Completed 1000 requests
	Finished 1000 requests


	Server Software:        Apache/2.4.18
	Server Hostname:        localhost
	Server Port:            80

	Document Path:          /phalcon/show
	Document Length:        954 bytes

	Concurrency Level:      1000
	Time taken for tests:   12.973 seconds
	Complete requests:      1000
	Failed requests:        120
	   (Connect: 0, Receive: 0, Length: 120, Exceptions: 0)
	Keep-Alive requests:    880
	Total transferred:      1091503 bytes
	HTML transferred:       839520 bytes
	Requests per second:    77.08 [#/sec] (mean)
	Time per request:       12972.721 [ms] (mean)
	Time per request:       12.973 [ms] (mean, across all concurrent requests)
	Transfer rate:          82.17 [Kbytes/sec] received

	Connection Times (ms)
	              min  mean[+/-sd] median   max
	Connect:        0   52 206.2      0    1001
	Processing:     6 3159 4164.3     22   12943
	Waiting:        6 3214 4251.5     22   12943
	Total:          6 3211 4241.3     22   12968

	Percentage of the requests served within a certain time (ms)
	  50%     22
	  66%   5003
	  75%   6058
	  80%   7198
	  90%  10023
	  95%  12872
	  98%  12945
	  99%  12960
	 100%  12968 (longest request)
	 
**关键词**

`Concurrency Level` 并发等级  
`Time taken for tests` 所有请求被处理完成所花费的时间总和  
`Complete requests` 总请求数  
`Keep-Alive requests`   
`Total transferred` 所有请求的响应数据长度总和  
`HTML transferred` 所有请求的响应数据中正文数据的总和，也就是减去了Total transferred 中的HTML响应数据中头信息的长度  

`Requests per second: 16.54 [#/sec] (mean)`  
表示当前测试的服务器每秒可以处理16.54个静态html的请求事务，后面的mean表示平均。这个数值表示当前机器的整体性能，值越大越好。

`Time per request: 60443.585 [ms] (mean)`  
单个并发的延迟时间，后面的mean表示平均。
隔离开当前并发，单独完成一个请求需要的平均时间。


