# study-notes

图解学习笔记，大图少字。在线阅读：https://archeu.github.io/study-notes/

分两个板块：**AI Agent 工程师**是主线，按学习地图一站一站走；**Java 后端架构**是之前的全部笔记，作为主线的补给库，按技术栈分层（架构与性能、框架、存储与消息、Java 平台、网络）。首页有两个板块的入口、技术栈地图、最近新增和搜索。

# AI Agent 工程师（主线）

| # | 页面 | 内容 |
|---|------|------|
| 00 | [AI Agent 学习地图](https://archeu.github.io/study-notes/agent/roadmap.html) | 从 Java 后端到 AI Agent 工程师（v2.1，对照 26 份招聘要求修订，每站先看场景全景）：四个等级、十二站路线（99 个知识点、过关检验、补给站）、招聘要求统计图、贯穿项目值班助手、17 个 AI 概念的 Java 比方、每周 26 小时的节奏和 30 周时间表、已有 44 篇的去向，先定位搜索 |
| 01 | [全景：一个 FastAPI 请求的一生](https://archeu.github.io/study-notes/agent/pano-01-fastapi-request.html) | 站 01 的场景全景：一条 curl 进 FastAPI，经过 uv、uvicorn、路由、参数校验、端点协程、gather、事件循环、解析日志、响应模型、pytest 十站，每站挂上 Python 速成的知识点和 Java 对照；并发与串行耗时实测、order-04 超时、阻塞调用卡住事件循环，分步演示 |
| 02 | [uv 管环境和依赖（对照 Maven）](https://archeu.github.io/study-notes/agent/python-uv.html) | 站 01 第 1 个知识点：pyproject 写意图、uv.lock 钉死整棵依赖树、.venv 按锁算出来并从全局缓存硬链接；对照 Maven 的 classpath 和最近者优先，pip 与 uv 建环境耗时实测，九个坑、团队规范、CI 与 Docker 写法，uv run 先猜再跑实验台 |
| 03 | [全景：一句话怎么变成模型的回答](https://archeu.github.io/study-notes/agent/pano-02-prompt-to-answer.html) | 站 02 的场景全景：值班助手把 order-04 的 GC 日志交给模型，经过拼请求、分词、上下文窗口、查向量表、读完输入（注意力与 KV 缓存）、算概率、采样、逐 token 循环、停下、结算核对十站，每站挂上知识点和 Java 对照；本机小模型实测分词、候选概率、温度 0 和 1、输入长度与耗时、前缀缓存、幻觉，分步演示 |
| 04 | [语法对照：列表、字典、推导式、切片](https://archeu.github.io/study-notes/agent/python-collections.html) | 站 01 第 2 个知识点：对照 Java 讲列表和字典的内存布局、推导式和生成器、切片为什么复制而不是视图、8 个坑、推导式与生成器的速度和内存实测，切片实验台 |
| 05 | [函数是一等公民：闭包和装饰器](https://archeu.github.io/study-notes/agent/python-closure-decorator.html) | 站 01 第 3 个知识点：函数是对象、闭包的 cell 和迟绑定、装饰器就是 f = deco(f) 且在 import 时从下往上执行、monkeypatch 改的是哪个模块的名字；对照 Java lambda 和 Spring AOP 代理，8 个坑本机复现，装饰器实验台（顺序 × wraps × 同步异步，8 种组合 FastAPI 实测） |
| 06 | [类型标注和 Pydantic 数据模型](https://archeu.github.io/study-notes/agent/python-pydantic.html) | 站 01 第 4 个知识点：类型标注是运行时不检查的元数据、Pydantic 在类定义时编译出校验器、宽松和严格模式、FastAPI 入口 422 与出口 response_model 过滤；对照 Java 编译器、Jackson 和 Bean Validation，8 个坑本机复现，校验耗时实测，Pydantic 实验台（10 种输入 × 两种模式） |
| 07 | [asyncio：事件循环、async/await、并发请求](https://archeu.github.io/study-notes/agent/python-asyncio.html) | 站 01 第 5 个知识点：协程是能在 await 处暂停的函数、事件循环用一个线程加 epoll 同时等很多 socket、gather 与 TaskGroup 出错时的区别、超时和取消是协作式的；对照 Java 线程池、Netty 和虚拟线程，阻塞与 GIL 实测，8 个坑，“一个线程的时间线”实验台 |
| 08 | [FastAPI 写接口（对照 Spring MVC）](https://archeu.github.io/study-notes/agent/python-fastapi.html) | 站 01 第 6 个知识点：uvicorn、Starlette、FastAPI 三层分工，签名决定参数从路径、查询串、请求体还是依赖来，Depends、lifespan 共享连接池、def 端点的 40 线程上限；值班助手加假日志代理的真服务实测，7 个坑，“参数从哪来”实验台 |
| 09 | [pytest 写测试](https://archeu.github.io/study-notes/agent/python-pytest.html) | 站 01 第 7 个知识点：按名字收集、assert 改写、按参数名注入的 fixture 和作用域、dependency_overrides 加 MockTransport 不起外部服务测接口；对照 JUnit、Mockito、MockMvc，10 个测试先红后绿抓到一个真 bug，8 个坑，fixture 作用域实验台 |

# Java 后端架构（补给库）

| # | 页面 | 内容 |
|---|------|------|
| 00 | [Java 后端架构学习地图](https://archeu.github.io/study-notes/java/roadmap.html) | 从高级工程师到架构师（每站先看场景全景，J04 用“从输入 URL 到页面展示”）：三个等级、十六站路线（117 个知识点，J06 含 PostgreSQL 对照，J11 含 TiDB、OceanBase、GoldenDB、过关检验、待做页）、25 份招聘要求统计和已有页面的缺口、交易靶场贯穿、两段式安排（AI 主线期间按需补，走完后约 15 周系统学）、版本基线，先定位搜索 |

## Spring

| # | 页面 | 内容 |
|---|------|------|
| 01 | [Spring MVC 请求关卡](https://archeu.github.io/study-notes/spring/spring-web-gates.html) | Filter、Interceptor、WebMvcConfigurer 的区别、生命周期和用途 |
| 02 | [Spring AOP 与事务](https://archeu.github.io/study-notes/spring/spring-aop-tx.html) | 代理、切面、通知，@Transactional 的提交回滚、传播、隔离和失效场景 |
| 03 | [Spring Boot 自动配置](https://archeu.github.io/study-notes/spring/spring-boot-autoconfig.html) | starter、自动配置清单、条件注解，启动时序和自定义 starter |
| 04 | [Bean 生命周期与循环依赖](https://archeu.github.io/study-notes/spring/spring-bean-lifecycle.html) | 十四站生命周期、回调顺序、作用域，三级缓存怎么解循环依赖 |
| 05 | [Spring Security 认证与授权](https://archeu.github.io/study-notes/spring/spring-security.html) | 过滤器链、核验台、工牌和门禁，401 和 403 从哪来，Security 5 和 6 的写法差别 |
| 06 | [Spring MVC 请求处理流程](https://archeu.github.io/study-notes/spring/spring-mvc-flow.html) | DispatcherServlet 的 doDispatch 八步，参数解析、页面和 JSON 两种返回、异常善后 |
| 07 | [Spring Boot 启动流程](https://archeu.github.io/study-notes/spring/spring-boot-startup.html) | run() 的四段路、refresh 十二步、Tomcat 什么时候开端口，事件顺序、扩展点和启动失败 |
| 08 | [Spring 事件机制](https://archeu.github.io/study-notes/spring/spring-events.html) | 发布者、广播站、监听器，同步、@Async、@TransactionalEventListener 怎么选，事件实验台 |
| 09 | [Spring IoC 与依赖注入](https://archeu.github.io/study-notes/spring/spring-ioc-di.html) | 容器里有什么、图纸从哪来、三种注入写法，同类型多个 Bean 时怎么选的注入裁判 |
| 10 | [Spring AOP 代理原理](https://archeu.github.io/study-notes/spring/spring-aop-proxy.html) | 替身什么时候换上、JDK 代理和 CGLIB、调用怎样穿过拦截器链，替身管不到的地方 |
| 11 | [Spring @Async 与线程池](https://archeu.github.io/study-notes/spring/spring-async-pool.html) | @Async 背后的派单员、用哪个线程池、四步规则和拒绝策略，线程池模拟器 |

## MyBatis

| # | 页面 | 内容 |
|---|------|------|
| 01 | [MyBatis 执行流程](https://archeu.github.io/study-notes/mybatis/mybatis-flow.html) | 启动时编好 SQL 手册，一次调用经过 MapperProxy、SqlSession、Executor 和 JDBC，两级缓存、#{} 与 ${}、插件 |
| 02 | [MyBatis 与 Spring 事务](https://archeu.github.io/study-notes/mybatis/mybatis-spring-tx.html) | 同一个 DataSource、线程上的储物柜、SqlSessionTemplate 复用会话，谁来提交，五个剧情看回滚和坑 |
| 03 | [MyBatis 插件与分页](https://archeu.github.io/study-notes/mybatis/mybatis-plugin-page.html) | 四个能拦的对象、Plugin.wrap 套娃和登记顺序，PageHelper 和 MyBatis-Plus 怎么分页，深分页 |
| 04 | [MyBatis 缓存与 Caffeine](https://archeu.github.io/study-notes/mybatis/mybatis-cache.html) | 一级、二级缓存怎么存怎么清，五个剧情看旧数据，和 Caffeine 逐项对比，LRU 与 W-TinyLFU 命中率 |
| 05 | [MyBatis-Plus 原理](https://archeu.github.io/study-notes/mybatis/mybatis-plus.html) | 启动时注入 SQL、Wrapper 怎么变成 SQL、自动填充和雪花 ID、插件总管和顺序，saveBatch 怎么批量 |

## 数据库

| # | 页面 | 内容 |
|---|------|------|
| 01 | [连接池与事务性能](https://archeu.github.io/study-notes/database/db-pool-tx-perf.html) | 为什么建连接贵、池子开多大、事务怎么吃掉连接、提交落盘和长事务、驱动参数，连接池模拟器 |
| 02 | [MySQL MVCC 与锁](https://archeu.github.io/study-notes/database/mysql-mvcc-lock.html) | 隐藏列和版本链、Read View 怎么判断看得见、快照读和当前读、四种行锁和死锁，MVCC 实验台和锁地图 |
| 03 | [HikariCP ConcurrentBag 源码](https://archeu.github.io/study-notes/database/hikari-concurrentbag.html) | 口袋、货架、递交窗口和 state CAS、为什么借连接不加锁却不保证先来先得、先改 state 再看 waiters、逐行读 borrow / requite、各版本差异，线程调度实验台 |

## 性能

| # | 页面 | 内容 |
|---|------|------|
| 01 | [系统压测](https://archeu.github.io/study-notes/perf/load-testing.html) | 看哪五个数、六种压测、吞吐为什么会到顶、八类常见瓶颈的原理和解法、方案优劣和工具对比，压测曲线和瓶颈实验台 |
| 02 | [响应时间为什么越压越长](https://archeu.github.io/study-notes/perf/response-time-queueing.html) | 六步排查：RT 的账单、四问排查路线、一串窗口和浴缸、开环积压与出口变窄、超时重试的反馈环、排队还是拒绝，四个本机实验和排队实验台 |

## Redis

| # | 页面 | 内容 |
|---|------|------|
| 01 | [缓存穿透、击穿与雪崩](https://archeu.github.io/study-notes/redis/cache-problems.html) | 三种漏法怎么发生、布隆过滤器、互斥锁和逻辑过期、过期时间打散和高可用，十种防护的代价，数据库压力实验台 |
| 02 | [Redis 持久化 RDB 与 AOF](https://archeu.github.io/study-notes/redis/redis-persistence.html) | 拍照和记账、fork 与写时复制、三种刷盘策略、AOF 重写、混合持久化和多文件 AOF，宕机实验台 |
| 03 | [Redis 主从、哨兵与集群](https://archeu.github.io/study-notes/redis/redis-ha-cluster.html) | 全量和部分同步、哨兵怎么判死和换主、16384 个槽和 hash tag，故障转移演示和槽位计算器 |
| 04 | [Redis 数据结构与编码](https://archeu.github.io/study-notes/redis/redis-data-encoding.html) | 五种类型和八种编码、SDS 与 embstr、listpack 与 quicklist、渐进式 rehash、跳表，编码观察器 |
| 05 | [Redis 过期删除与内存淘汰](https://archeu.github.io/study-notes/redis/redis-eviction-expire.html) | 惰性删除加定期巡逻、八种淘汰策略、近似 LRU 的抽样和候选池、LFU 计数器，巡逻实验台和淘汰准确度对比 |
| 06 | [Redis 分布式锁](https://archeu.github.io/study-notes/redis/redis-distributed-lock.html) | 五次进化、令牌和 Lua 解锁、Redisson 看门狗，锁与事务的顺序、主从切换丢锁、RedLock 和 fencing token，事故实验台 |
| 07 | [Redis 线程模型与 IO 多路复用](https://archeu.github.io/study-notes/redis/redis-threading-io.html) | 单线程为什么快、select/poll/epoll、事件循环演示、慢命令怎么堵住所有人、I/O 线程和 Pipeline |
| 08 | [Redis 大 key 与热 key](https://archeu.github.io/study-notes/redis/redis-bigkey-hotkey.html) | 多大算大、危害和拆分，热 key 为什么加机器没用、本地缓存和复制打散，怎么发现，大 key 计算器和热 key 实验台 |
| 09 | [Redis Stream 与消息队列](https://archeu.github.io/study-notes/redis/redis-stream-mq.html) | List、Pub/Sub、Stream 三代对比，消费组、PEL、ACK 和认领，至少一次与幂等，延迟消息，消费组实验台 |
| 10 | [Redis Lua 脚本与事务](https://archeu.github.io/study-notes/redis/redis-lua-tx.html) | MULTI/EXEC/WATCH、出错为什么不回滚、Lua 的写法和 EVALSHA、Redis 7 Functions，最后一件库存两人抢 |
| 11 | [布隆过滤器与 HyperLogLog](https://archeu.github.io/study-notes/redis/redis-bloom-hll.html) | 位数组和 k 个哈希、误判率实验室、容量怎么算、抛硬币估人数、16384 个桶，UV 统计和选型 |

## Kafka

| # | 页面 | 内容 |
|---|------|------|
| 01 | [Kafka 消息可靠性与消费组](https://archeu.github.io/study-notes/kafka/kafka-reliability-group.html) | 六步学习法：acks 和 ISR、min.insync.replicas、offset 提交时机、消费组和 rebalance、幂等与死信，故障实验台和消费组实验台（关键行为本机集群实测） |
| 02 | [Kafka 存储：segment、索引、页缓存与零拷贝](https://archeu.github.io/study-notes/kafka/kafka-storage-zerocopy.html) | 分段和稀疏索引怎么查、页缓存为什么比 JVM 缓存好、sendfile 少了哪几次拷贝、retention 为什么不准、回放拖慢实时和 TLS 的代价，查找、零拷贝、页缓存三个实验台 |

## Java 并发

| # | 页面 | 内容 |
|---|------|------|
| 01 | [SynchronousQueue 与 LinkedTransferQueue](https://archeu.github.io/study-notes/juc/synchronous-transfer-queue.html) | 双重队列和双重栈、一次 CAS 完成交接、xfer 的四种模式、先自旋再 park、slack 与自链接、线程池里的后果、JDK 11 / 21 实测，分步演示和沙盘 |
| 02 | [ThreadPoolExecutor.execute 源码](https://archeu.github.io/study-notes/juc/threadpool-execute.html) | execute 的三个 if、ctl 的位、Worker 和 getTask、放进队列后的复查和线程退出前的检查、几件只能靠源码解释的怪事、各版本差异，线程调度实验台 |
| 03 | [AQS 源码](https://archeu.github.io/study-notes/juc/aqs.html) | state 加等待队列、独占和共享、Condition 的两条队、公平与非公平、JDK 8 和 17 / 21 两代源码对照、日常开发里哪些框架和 JDK 类用到了它，三个 JDK 实测和实验台 |
| 04 | [Java 内存模型](https://archeu.github.io/study-notes/juc/java-memory-model.html) | 写了不等于别人看到：重排序从哪来、happens-before 规则和推导、为什么只保证没有数据竞争的程序、volatile / synchronized / final 各保证什么、内存屏障和 VarHandle，可见性和重排序实测（JDK 17，ARM），双重检查锁分步推演 |

## 网络

| # | 页面 | 内容 |
|---|------|------|
| 01 | [从输入 URL 到页面展示](https://archeu.github.io/study-notes/network/url-to-page.html) | 12 站全景、往返次数尺子、DNS 层级缓存、TCP + TLS 1.3 时序、慢启动、渲染阻塞、三次握手等设计取舍、Java 迷你浏览器实测（JDK 8 / 17 / 21）、往返计算器和 script 位置实验台 |
| 02 | [网络 IO 模型](https://archeu.github.io/study-notes/network/io-models.html) | 一万个连接要几个线程：五种 IO 模型的两段等待、连接便宜线程贵、Reactor 和 Tomcat NIO 连接器、事件循环为什么不能阻塞、HTTP 连接池和 keep-alive 等八个坑、BIO / NIO / 虚拟线程 1 万连接实测（JDK 17 / 21），keep-alive 连接分步演示 |

## 架构

| # | 页面 | 内容 |
|---|------|------|
| 01 | [三高知识地图](https://archeu.github.io/study-notes/arch/three-highs-map.html) | 高性能、高并发、高可用是同一本账：Little 定律算线程和连接、可用率串联相乘并联互补、超时舱壁降级为什么缺一不可、知识点挂在请求链路（含网络 IO、服务治理）和投产六关上、日常开发和投产两张清单、积分卡住时四种写法实测，线程账实验台 |

## JDK

| # | 页面 | 内容 |
|---|------|------|
| 01 | [JDK 8、17、21、25](https://archeu.github.io/study-notes/jdk/jdk-8-17-21.html) | 四个 LTS 是怎么连起来的：5、6、7 留下的地基（内存模型、锁优化、invokedynamic、Fork/Join）、半年一班车和预览特性、四条主线（语言、并发、GC、平台治理）、50 个新特性各是什么、为什么加、怎么用（带示例）、record + sealed + 模式匹配、强封装、ScopedValue 的设计取舍、8 / 21 / 25 写法对照与升级五步、十二个升级坑、25 之后的 27 和 29，升级检查器 |

## JVM

| # | 页面 | 内容 |
|---|------|------|
| 01 | [JVM 内存结构](https://archeu.github.io/study-notes/jvm/jvm-memory-structure.html) | 一个 Java 进程的内存分成哪几块：线程私有的栈、共享的堆、堆外的元空间和直接内存，栈和堆怎么配合、对象头和对象大小、为什么分代，六种 OOM 怎么认、容器被杀的原因，实测撑爆四块内存（JDK 17），分代实验台 |
| 02 | [G1 和 ZGC 怎么回收](https://archeu.github.io/study-notes/jvm/g1-zgc.html) | 回收的三件事谁要停下来做、G1 的 Region 和记忆集、并发标记与混合回收、停顿预测、ZGC 的染色指针、读屏障和并发搬迁、为什么一个停顿里搬一个边跑边搬、六个坑和版本差异，实测 Parallel、G1、ZGC 四组对比（JDK 17），G1 和 ZGC 实验台 |
