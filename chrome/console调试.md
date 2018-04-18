# console控制台调试教程

## 1.network Tab叶签
#### 时间线参数讲解
- `Stalled` 是浏览器得到要发出这个请求的指令，到请求可以发出的`等待时间`，一般是代理协商，以及等待可复用的TCP连接释放的时间，`也包括`DNS查询，建立TCP连接时间等。

- `Request sent` 请求第一个字节发出前到最后一个字节发出后的时间，也就是上传时间。
- `Waiting` 请求发出后，到收到响应的第一个字节所花费的时间(Time To First Byte)
- `Content Download`接收到响应的第一个字节，到接收完最后一个字节的时间，就是下载时间。


>#### 官网原文文档
>#####Stalled/Blocking
Time the request spent waiting before it could be sent. This time is
inclusive of any time spent in proxy negotiation. Additionally, this
time will include when the browser is waiting for an already
established connection to become available for re-use, obeying
Chrome's maximum six TCP connection per origin rule.

>#####Proxy Negotiation
Time spent negotiating with a proxy server connection.

>#####DNS Lookup
Time spent performing the DNS lookup. Every new domain on a pagerequires a full roundtrip to do the DNS lookup.

>#####Initial Connection / Connecting
Time it took to establish a connection, including TCPhandshakes/retries and negotiating a SSL.

>#####SSL
Time spent completing a SSL handshake.

>#####Request Sent / Sending
Time spent issuing the network request. Typically a fraction of amillisecond.

>#####Waiting (TTFB)
Time spent waiting for the initial response, also known as the Time To
First Byte. This time captures the latency of a round trip to the
server in addition to the time spent waiting for the server to deliver
the response.

>#####Content Download / Downloading
Time spent receiving the response data.

　
>[帮助文档连接（官方）](https://developers.google.com/web/tools/chrome-devtools/profile/network-performance/resource-loading#resource-network-timing)
>[原文链接](https://segmentfault.com/q/1010000002399481/a-1020000002399855)