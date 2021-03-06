

### 1、什么消息推送系统？

如：弹幕，聊天消息，通知等

### 2、推送技术复杂度

> 1个直播间
> 在线人数100万
> 发送弹幕1000条/秒

### 3、拉模式和推模式的区别

> 1. 拉模式：客户端主动身服务器请求
>    数据更新频率低，并且大多数请求是无效的。
>    在线用户数量多，服务端的查询负载高
>    定时拉取，无法满足时效性
>
> 2. 推模式：服务端向客户端主动推送数据
>    仅在数据更新时才推送数据
>    需要维护大量的在线长连接
>    数据更新后可以立即推送

### 4、基于WebSocket推送

> 浏览器支持的Socket编程，轻松维持服务端的长连接
> 基于TCP可靠传输之上的协议，无需开发者关心通讯细节
> 提供了高度抽象的编程接口，业务开发成本较低4、

### 5、通讯流程

客户端->发送upgrade到->服务器->响应switching给 ->客户端：相互之间建立了不中断的连接

### 6、传输原理

> 协议升级后，继续复用HTTP的底层Socket完成后续通讯
> Message 底层被切分成了多个Frame帧传输
> 编程时只需要操作Message，无需关心Frame
> 框架底层完成了TCP网络I/O，WebSocket协议解析，开发者无需关心

### 7、服务端的技术选型与考虑

> NodeJS ： 单线程模型，推送性能有限
> C/C++：TCP通讯、WebSocket协议实现成本高
> GO：多线程，基于协程模型并发。成熟的WebSocket标准库，无需造轮子

### 8、实现HTTP服务端

> WebSocket是HTTP协议Upgrader握手而来
> 使用Http标准库快速实现空接口：/ws

### 9、封装WebSocket

> 其他代码模块，无法直接 操作WebSocket连接
> WebSocket连接非线程安全，并发/读写需要同步
> 隐藏细节，封装API
> 封装Connection结构，隐藏WebSocket底层连接
> 封装Connection的API，提供Send/Read/Close等线程安全接口

### 10、API 原理

> SendMessage将消息投递到out channel
>  ReadMessage从in channel 读取消息

- 内部原理
  - 启动读协程：循环读取WebSocket，将消息投递到 in channel
  - 启动写协程：循环读取 out channel，将消息写给WebSocket

### 11、千万级弹幕系统的架构秘密

#### 1)技术难点

- 3个性能瓶颈
  - 内核瓶颈、锁瓶颈、CPU瓶颈

##### 内核瓶颈：

- 推送量大，内核瓶颈

##### 锁瓶颈：

- 需要维护大量的在线用户集合
- 推送消息即遍历整个用户集合，顺序发送消息，耗时极长
- 推送期间，客户端仍旧正常上下线，所以集合需要加锁

##### CPU瓶颈：

- 浏览器与服务端通常采取Json格式通讯
- Json编码非常耗费CPU资源

#### 2)技术难点的解决方案

> 内核瓶颈-优化原理
> 减少网络小包的发送

<font color=red>优化方案：</font>

- 将同一秒内的N条消息，合并成一条消息
- 合并后，每秒推送次数只等于在线连接数

##### 锁瓶颈-优化原理

- 大拆小

<font color=red>优化方案</font>

- 连接打散到多个集合中，每个集合有自己的锁
- 多线程并发推送多个集合，避免锁竞争
- 读写锁取代互斥锁，多个推送任务可以并发遍历相同集合

##### CPU瓶颈-优化原理

- 减少重复计算

<font color=red>解决方案</font>

- Json编码前置，1次消息编码+100万次推送
- 消息合并前置，N条消息合并后只编码1次

### 12、揭秘分布式架构

#### 单机瓶颈

- 维护少量长连接会花费不少内存
- 消息推送瞬时消耗大量CPU资源
- 消息推送瞬时带宽高达400~600MB，是主要瓶颈

#### 网关集群

#### 逻辑集群

- 基于HTTP/2协议向Gateway集群分发消息
  - HTTP/2支持连接复用，用作RPC性能更佳

- 基于HTTP/1协议对外提供推送API
  - HTTP/1更加普及，对业务方更加友好














