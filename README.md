# study-notes

图解学习笔记，大图少字。在线阅读：https://archeu.github.io/study-notes/

分两个板块：**AI Agent 工程师**是主线，按学习地图一站一站走；**Java 后端架构**是之前的全部笔记，作为主线的补给库，按技术栈分层（架构与性能、框架、存储与消息、Java 平台、网络）。首页有两个板块的入口、技术栈地图、最近新增和搜索。

配套代码在 [archeu/study-labs](https://github.com/archeu/study-labs)：页面上的快速入门、实测实验和练习，每页一个目录，克隆后用 IDE 打开就能跑（2026-11-09 之前的旧代码按原样收在 `legacy/`）。

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
| 10 | [用 AI 编程工具干活：Claude Code、Cursor](https://archeu.github.io/study-notes/agent/ai-coding-tools.html) | 站 01 第 8 个知识点（站末总结）：智能体循环、上下文窗口与 CLAUDE.md、checkpoint 和权限模式，复盘一次真实的修 bug，6 个在 ~/claude/oncall-helper 里亲手做的练习，“这件事交给 AI 吗”判断台 |

# Java 后端架构（补给库）

| # | 页面 | 内容 |
|---|------|------|
| 00 | [Java 后端架构学习地图](https://archeu.github.io/study-notes/java/roadmap.html) | 从高级工程师到架构师（每站先看场景全景，J04 用“从输入 URL 到页面展示”）：三个等级、十六站路线（117 个知识点，J06 含 PostgreSQL 对照，J11 含 TiDB、OceanBase、GoldenDB、过关检验、待做页）、25 份招聘要求统计和已有页面的缺口、交易靶场贯穿、两段式安排（AI 主线期间按需补，走完后约 15 周系统学）、版本基线，先定位搜索 |
| 01 | [全景：一个订单对象的一生](https://archeu.github.io/study-notes/java/pano-j01-order-object-life.html) | J01 的场景全景：用户 1024 下单 2 件 88 号商品，一个 Order 经过 Tomcat 收字节、Jackson 反序列化成 record、Spring 代理开事务、HashMap 查商品、new 实体与泛型擦除、Stream 和模式匹配算价、扣库存抛异常回滚、放进集合、DelayQueue、序列化写回、留在堆里十一站，每站挂上 J01 知识点；本机 Spring Boot 实测每站类名、桶下标、冷热耗时和存活对象数，分步演示 |
| 02 | [全景：一个下单请求在线程池里](https://archeu.github.io/study-notes/java/pano-j02-order-in-threadpool.html) | J02 的场景全景：1000 人抢 100 件 88 号键盘，一个请求经过 Tomcat Acceptor 和 Poller、exec 线程池、ThreadLocal 绑用户、读库存、写回撞车超卖，再分三种修法（synchronized、CAS、数据库条件更新），最后进 ConcurrentHashMap、CompletableFuture 异步通知、清 ThreadLocal 回池十一站，每站挂上 J02 知识点；本机 Spring Boot 实测五种写法的超卖件数、BLOCKED 线程数和虚拟线程，分步演示 |
| 03 | [全景：一个对象从 new 到被回收](https://archeu.github.io/study-notes/java/pano-j03-object-new-to-gc.html) | J03 JVM 与调优的场景全景：类加载、JIT 与逃逸分析、TLAB 分配、大对象、Young GC、晋升、并发标记与 Mixed GC、泄漏到 Full GC、OOM 排查、容器内存十站，附实测 GC 日志，分步演示 |
| 04 | [全景：订单服务调库存服务的一次 RPC](https://archeu.github.io/study-notes/java/pano-j04-order-calls-inventory.html) | J04 场景全景：Stub、服务发现与负载均衡、长连接、protobuf、HTTP/2 帧、Netty EventLoop、TCP、服务端 Reactor、业务线程池、deadline 十站，gRPC 对 HTTP/1.1 的延迟和连接数实测，分步演示 |
| 05 | [全景：一个请求穿过 Spring](https://archeu.github.io/study-notes/java/pano-j05-request-through-spring.html) | J05 场景全景：启动装配、Tomcat、Security 过滤器链、DispatcherServlet、参数解析、AOP 代理、事务拦截器、Mapper 代理、Executor 与插件、提交后事件、回程十一站，SQL 发出时 131 层调用栈和分段耗时实测（BCrypt 占 82 ms、自调用不回滚），分步演示 |
| 06 | [全景：一条 UPDATE 从应用到磁盘](https://archeu.github.io/study-notes/java/pano-j06-update-to-disk.html) | J06 场景全景：借连接、发 SQL、连接线程、解析优化、B+ 树找页、行锁、undo、改页写 redo、两阶段提交、回 OK、从库回放、刷脏页十二站，MySQL 8.4 一主一从实测（冷读 3 页、提交等落盘 3 ms、提交 120 秒后页仍是脏的），分步演示 |
| 07 | [全景：一次商品详情查询](https://archeu.github.io/study-notes/java/pano-j07-product-detail-cache.html) | J07 场景全景：查本地、发 GET、主线程查字典、布隆过滤器、重建锁、查库、回填加解锁、放本地、改价提交、删 Redis、广播失效、后台落盘淘汰十二站，Redis 8.10 + Caffeine + MySQL 8.4 实测（本地命中 4 µs、Redis 往返 279 µs 而服务端只要 2 µs、击穿时查库 1～26 次加锁后 1 次、改价后 11～26 ms 跟上），分步演示 |

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
| 12 | [代理是哪一刻换进容器的：Bean 生命周期下一圈](https://archeu.github.io/study-notes/spring/spring-bean-proxy-swap.html) | refresh 三段和 BPP 三组登记、代理在初始化最后一步换进去、@PostConstruct / 循环依赖 / BPP 提前建三条漏口、@Async 环的 raw version 和 Spring 6.2 的变化，九个场景的先猜再跑实验台 |
| 13 | [249 个 bean 是谁建的：Boot 自动配置与启动下一圈](https://archeu.github.io/study-notes/spring/spring-boot-bean-ledger.html) | 两道筛子（158→43→35）、249 个 bean 的账本、全景各站对象出自哪张图纸、“你没写我才写”的让位规矩、3.8 s 启动时间账、六个实测坑，七场景先猜再跑实验台 |
| 14 | [代理里那十几层在干什么：AOP 与代理下一圈](https://archeu.github.io/study-notes/spring/spring-aop-chain.html) | 调用栈 11 层逐层拆开、启动时链怎么过筛加头排序、@Async 插到第 0 位、下标走链与一个代理一条链的设计、计时漏算提交和重试切面在事务里等四个坑、每层开销粗测与 6.1/6.2、JDK 17/21 差异，排链先猜再跑实验台 |
| 15 | [付款失败，流水要不要一起撕：事务传播、隔离与失效下一圈](https://archeu.github.io/study-notes/spring/spring-tx-propagation.html) | 进门先问线程上有没有事务、三种传播在连接上的样子、提交六步和提交后写库、REQUIRES_NEW 借空连接池和自锁、隔离和超时何时生效、Spring 6.0～7.0 护栏，3×4 付款组合先猜再跑实验台 |
| 16 | [一个 400 进了两次 DispatcherServlet](https://archeu.github.io/study-notes/spring/spring-mvc-dispatch.html) | Spring MVC 请求处理下一圈：分派类型与 /error 再分派、过滤器按分派登记的两层开关、拦截器调两次、Boot 3 公开接口出错变 401、过滤器重复注册、冷热请求时间账，八个场景的分派演示 |
| 17 | [付款一次算一遍密码：Spring Security 认证与授权下一圈](https://archeu.github.io/study-notes/spring/spring-security-token.html) | BCrypt 为什么故意慢和 cost 实测、登录一次换会话或 JWT、JWT 怎么验（签名、60 秒偏差、SCOPE_ 前缀）、@PreAuthorize 按数据授权、显式保存、会话固定、登出撤销六个坑，凭证实验台 |
| 18 | [改个版本号，付款就 400 了：Spring Boot 3 到 4、Jakarta 与 Jackson 3 升级](https://archeu.github.io/study-notes/spring/spring-boot4-upgrade.html) | 编译器看得见的改名和看不见的默认值、Jackson 3 怎么换掉第 5 站、MyBatis 旧 starter 为何找不到 Mapper、六个坑和五个练习，四种构建 × 六个付款请求的先猜再跑实验台 |
| 19 | [测试全绿，付款照样没回滚：JUnit 5、Mockito 与 Testcontainers](https://archeu.github.io/study-notes/spring/spring-testing.html) | JUnit 5 平台和扩展、Mockito 的答案表和录像带、Web / MyBatis 切片和上下文缓存、Testcontainers 起真 MySQL、三颗事务雷只有真库整链测试抓得到、测试类加 @Transactional 全部失真、Boot 4 测试依赖变化，测试层 × 写法实验台 |

## MyBatis

| # | 页面 | 内容 |
|---|------|------|
| 01 | [MyBatis 执行流程](https://archeu.github.io/study-notes/mybatis/mybatis-flow.html) | 启动时编好 SQL 手册，一次调用经过 MapperProxy、SqlSession、Executor 和 JDBC，两级缓存、#{} 与 ${}、插件 |
| 02 | [MyBatis 与 Spring 事务](https://archeu.github.io/study-notes/mybatis/mybatis-spring-tx.html) | 同一个 DataSource、线程上的储物柜、SqlSessionTemplate 复用会话，谁来提交，五个剧情看回滚和坑 |
| 03 | [MyBatis 插件与分页](https://archeu.github.io/study-notes/mybatis/mybatis-plugin-page.html) | 四个能拦的对象、Plugin.wrap 套娃和登记顺序，PageHelper 和 MyBatis-Plus 怎么分页，深分页 |
| 04 | [MyBatis 缓存与 Caffeine](https://archeu.github.io/study-notes/mybatis/mybatis-cache.html) | 一级、二级缓存怎么存怎么清，五个剧情看旧数据，和 Caffeine 逐项对比，LRU 与 W-TinyLFU 命中率 |
| 05 | [MyBatis-Plus 原理](https://archeu.github.io/study-notes/mybatis/mybatis-plus.html) | 启动时注入 SQL、Wrapper 怎么变成 SQL、自动填充和雪花 ID、插件总管和顺序，saveBatch 怎么批量 |
| 06 | [100 笔订单发出 101 条 SQL：MyBatis 结果映射、N+1 与流式查询](https://archeu.github.io/study-notes/mybatis/mybatis-result-mapping.html) | JOIN 的行怎么靠 <id> 折叠成对象、嵌套查询的 N+1、懒加载代理在事务外每次借连接、明细字段全 null、JOIN 后分页少订单、Cursor 离不开事务和驱动 fetchSize、分页导出被一级缓存拽住，8 组交易靶场实测和逐行折叠演示 |

## 数据库

| # | 页面 | 内容 |
|---|------|------|
| 01 | [连接池与事务性能](https://archeu.github.io/study-notes/database/db-pool-tx-perf.html) | 为什么建连接贵、池子开多大、事务怎么吃掉连接、提交落盘和长事务、驱动参数，连接池模拟器 |
| 02 | [MySQL MVCC 与锁](https://archeu.github.io/study-notes/database/mysql-mvcc-lock.html) | 隐藏列和版本链、Read View 怎么判断看得见、快照读和当前读、四种行锁和死锁，MVCC 实验台和锁地图 |
| 03 | [HikariCP ConcurrentBag 源码](https://archeu.github.io/study-notes/database/hikari-concurrentbag.html) | 口袋、货架、递交窗口和 state CAS、为什么借连接不加锁却不保证先来先得、先改 state 再看 waiters、逐行读 borrow / requite、各版本差异，线程调度实验台 |
| 04 | [100 万行里找 9527，只读了 3 页：索引与 B+ 树](https://archeu.github.io/study-notes/database/mysql-index-bplustree.html) | 页和 B+ 树为什么只有 3 层、页目录二分、聚簇索引和二级索引、回表与覆盖索引、联合索引最左前缀、为什么二级索引存主键，读 .ibd 数树形和拿页次数实测，查询走法演示 |
| 05 | [明明有索引，它偏不走：执行计划与 SQL 调优](https://archeu.github.io/study-notes/database/mysql-explain-tuning.html) | 慢查询日志与按指纹汇总、EXPLAIN 各列、EXPLAIN ANALYZE 对估算、代价模型与回表分界点实测、索引失效六种写法、深分页与游标分页，16 种写法先猜再看实验台 |
| 06 | [两次付款同时到，第二次改了 0 行：事务、MVCC 与锁（下一圈）](https://archeu.github.io/study-notes/database/mysql-lock-wait-deadlock.html) | 快照读与当前读、等锁醒来后重新判断 WHERE、三种 WHERE 在 RR / RC 下锁了多少行、1205 只回滚一条语句、死锁日志怎么读，连点两次付款实验台 |
| 07 | [commit 返回了，数据页还是旧的：redo、undo、binlog 与两阶段提交](https://archeu.github.io/study-notes/database/mysql-redo-undo-binlog.html) | WAL 与检查点、undo 版本链与 purge、binlog 与 redo 的分工、两阶段提交和崩溃恢复规则、提交途中 kill -9 三次实测、redo 容量与长事务实测，崩溃点实验台 |
| 08 | [付完款跳回订单页，还是待付款：主从复制、读写分离与复制延迟](https://archeu.github.io/study-notes/database/mysql-replication-lag.html) | 三个线程两份日志、GTID、延迟拆成传排队回放、大事务与心跳曲线、从库被写停在 1032、读写分离三种写后读，路由实验台 |
| 09 | [orders 加一列，支付接口全卡住了：表结构设计与大表变更（Online DDL）](https://archeu.github.io/study-notes/database/mysql-online-ddl.html) | 建表时每个类型的改表代价、INSTANT / INPLACE / COPY 三种算法、元数据锁排队、DDL 到从库再做一遍、gh-ost 影子表对照，一边付款一边改表的实测，改表计划台 |
| 10 | [池子从 10 开到 50，付款一点没快：连接池与事务性能（下一圈）](https://archeu.github.io/study-notes/database/db-pool-tx-perf-hot-row.html) | 热点行吞吐 ≈ 1 ÷ 持锁时间、队伍从 HikariCP 挪进 InnoDB、组提交为什么在热点行上凑不成组、8 组靶场实测和池子 1～64 曲线，三开关实验台 |
| 11 | [换上 8.4，付款服务连不上库了：MySQL 8.0 升级 8.4 LTS](https://archeu.github.io/study-notes/database/mysql-84-upgrade.html) | 8.0 停更与 LTS 发布模型、启动时自动升级且单向、先升从库再切换、账号插件 / MASTER-SLAVE 语法 / 默认值 / 外键四类变化、caching_sha2_password 缓存、交易靶场全程实测，连接实验台 |
| 12 | [订单表一行没加，PG 里却胖了一倍：PostgreSQL 的多版本、VACUUM、索引类型和 JSONB](https://archeu.github.io/study-notes/database/pg-mvcc-vacuum-jsonb.html) | PG 不原地改行、旧版本留在表里、可见性与回滚、页内修剪 / VACUUM / autovacuum / VACUUM FULL、长事务挡住清理、HOT 与 fillfactor、xid 冻结、B-tree / BRIN / GIN / 部分索引与表达式索引、JSONB 与 GIN，全部在 PG 18.7 上实测，堆表实验台 |
| 13 | [工单库要加“找相似故障”：MySQL 还是 PostgreSQL，pgvector 凭什么](https://archeu.github.io/study-notes/database/mysql-vs-pg-pgvector.html) | MySQL 和 PG 逐项对比、向量放哪的五种方案和选择规则、PG 扩展的四个插槽（类型、运算符、运算符类、索引访问方法）、带过滤查询的执行路径、为什么 MySQL 社区版做不出向量索引、本机实测带条件少行和三种补法，过滤 HNSW 实验台 |

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
| 12 | [改完价，详情页还卖 399：先改库还是先删缓存、延迟双删、订阅 binlog](https://archeu.github.io/study-notes/redis/cache-consistency.html) | 先删后改为什么必卡、删不改、先改后删剩下的慢读竞态、延迟双删、订阅 binlog 删缓存、墓碑加版本号回填、交易靶场 6 种写法实测，竞态推演台 |
| 13 | [4 台机器各存一份 88 号：Caffeine 加 Redis 两级缓存](https://archeu.github.io/study-notes/redis/cache-multilevel.html) | 两级缓存读写路径、为什么广播删除再配短过期、先删 Redis 再广播、get(key, loader) 和桶锁、订阅断线丢消息与断线即清、CLIENT TRACKING / Redisson / JetCache 对比、refreshAfterWrite 版本差异，两级缓存推演台 |
| 14 | [88 号过期那一刻：缓存穿透、击穿、雪崩与大 key、热 key](https://archeu.github.io/study-notes/redis/cache-five-holes.html) | J07 第 3 个下钻知识点（第二圈）：交易靶场里实测穿透、击穿、雪崩三组对比，挡在前面、排队、打散、允许旧四类防法的取舍，重建锁对逻辑过期，大 key 堵住共享连接，HOTKEYS 找热 key，DEL 对 UNLINK，击穿实验台 |
| 15 | [锁过期时 A 还在查库：看门狗、fencing token 与 Lua 条件写](https://archeu.github.io/study-notes/redis/redis-lock-expire-fencing.html) | 锁是租约所以会过期、A 自己判断为什么不行、锁守卫与版本守卫（fencing token）、DEL 换墓碑、Redisson 看门狗挡不住进程停住、Lua 脚本 BUSY 与 NOSCRIPT、Redlock 之争，三条时间线 × 五种回填写法实验台 |
| 16 | [279 µs 里只有 2 µs 在 Redis：一条连接、一个线程上的排队](https://archeu.github.io/study-notes/redis/redis-event-loop-queueing.html) | J07 全景第 2、3 站下钻（第二圈）：一次 GET 拆成 8 段、主线程和共享连接两处排队、KEYS / BLPOP / 大 value 谁拖住谁、SLOWLOG 为什么看不见排队、IO 线程 7.2 到 8.x、Lettuce 超时与 FIFO 队列，谁会卡住实验台 |
| 17 | [648 字节的详情占 805 字节：Redis 8 的 kvobj、embstr 新门槛与存 String 还是 Hash](https://archeu.github.io/study-notes/redis/redis-encoding-memory.html) | J07 全景第 7 站第二圈：805 字节逐块拆解、Redis 7.2 和 8.2+ 一个 key 的两种拼法、embstr 门槛变成 key + 值 ≤ 41、String / Hash / JSON 四种存法实测、四个内存坑，字符串 key 内存计算器 |
| 18 | [第 617 个商品写不进去：Redis 写满以后的 OOM、淘汰与过期](https://archeu.github.io/study-notes/redis/redis-oom-eviction.html) | J07 第二圈：maxmemory 写满时哪些命令被拒（DENYOOM、Lua 脚本）、四种策略在交易靶场里赶走谁（连锁也赶）、过期 key 晚删造成的 OOM 窗口、淘汰时间预算与主动过期源码，全景链路实验台 |
| 19 | [88 号的锁有了两个主人：Redis 重启、切主以后丢了什么](https://archeu.github.io/study-notes/redis/redis-restart-failover.html) | J07 第二圈：一条 SET 回 OK 时在哪几处、重启时的 LOADING、切主丢掉的那一段、主库自动重启清空从库；Redis 8.10.3 实测四种持久化重启耗时、断网切主后锁有两个主人，附故障实验台 |

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
| 05 | [线程、线程状态与上下文切换](https://archeu.github.io/study-notes/juc/thread-state-context-switch.html) | Java 线程和内核线程 1:1、线程创建成本、六种状态和内核状态对照（RUNNABLE 也可能在 IO 里睡着）、读线程转储、两种上下文切换和怎么数、线程数公式、中断和守护线程，JDK 17 实测（/proc 对照、512 线程慢 36%、一次交接 3.9 微秒、新建线程 82 微秒），线程状态机实验台 |
| 06 | [JMM 下一圈：jcstress、CPU 缓存与伪共享](https://archeu.github.io/study-notes/juc/jmm-jcstress-cache.html) | Java 内存模型的下一圈：存储缓冲和失效队列、缓存一致性只管同一地址、x86 TSO 和 ARM 放宽了哪些重排序、volatile 和 CAS 在两种 CPU 上的指令、AQS 和 ConcurrentHashMap 里 volatile 读加 CAS 的模式、伪共享和 LongAdder；jcstress 0.16 在 ARM 上实测库存超卖（volatile 33.6%）、SB、MP（看到标志没看到数据 0.07%）和禁止结果 0 次，伪共享实测，先猜再看结果的实验台 |
| 07 | [synchronized 与锁升级、CAS 与原子类](https://archeu.github.io/study-notes/juc/synchronized-cas-atomic.html) | 对象头 mark word 的几种状态（JOL 实测无锁、thin lock、fat lock、偏向）、monitorenter / monitorexit 和异常表、轻量级锁和膨胀成 ObjectMonitor、wait / notify、偏向锁为什么被拿掉、CAS 在 ARM 和 x86 上的指令、ABA 实测、原子类和 LongAdder，五种写法吞吐实测（JDK 17，2 核 ARM），锁升级分步演示 |
| 08 | [AQS 下一圈：读写锁、StampedLock、Semaphore 与 JFR 找锁竞争](https://archeu.github.io/study-notes/juc/aqs-rwlock-jfr.html) | AQS 的下一圈：读写锁把 state 劈成两半、readerShouldBlock 和写锁饥饿、锁降级和升级死锁、StampedLock 乐观读和 validate、Semaphore 舱壁、JFR 的 jdk.JavaMonitorEnter / jdk.ThreadPark；JDK 17 实测四把锁读吞吐（读短时读写锁比普通锁慢、公平读写锁慢 75 倍、乐观读最快）、用 JFR 抓出锁里慢 SQL、Semaphore 限并发，先猜再看的实验台 |
| 09 | [ConcurrentHashMap 与阻塞队列](https://archeu.github.io/study-notes/juc/chm-blocking-queue.html) | HashMap 并发 put 丢数据实测（丢 4%～16%）、ConcurrentHashMap 的桶数组和三种特殊节点、putVal 的几条路（空桶 CAS、锁桶头、协助扩容）、TreeBin、分格计数、只保证单个方法原子（get 再 put 实测丢更新、merge 不丢）、Recursive update、初始容量，阻塞队列家族和 DelayQueue，JDK 17 反射实测，putVal 路径演示 |
| 10 | [线程池下一圈：怎么配、拒绝策略、动态调参与监控](https://archeu.github.io/study-notes/juc/threadpool-tuning.html) | 线程池的下一圈：用利特尔法则和 CPU 占比算线程数、按可接受排队时间定队列、四种拒绝策略把代价给了谁（实测 100 条通知三种策略丢 86 条、CallerRuns 让提交方慢 40 倍）、运行中先调最大再调核心（实测 2→16 积压 1 秒消完）、监控五个数、优雅关闭三步，参数计算器 |
| 11 | [ThreadLocal 与内存泄漏](https://archeu.github.io/study-notes/juc/threadlocal-leak.html) | 值存在线程的 ThreadLocalMap、key 弱 value 强的引用链、串号和三种泄漏、顺手清理与为什么不用引用队列、InheritableThreadLocal / TTL / ScopedValue，ThreadLocalMap 实验台 |
| 12 | [CompletableFuture 与异步编排](https://archeu.github.io/study-notes/juc/completablefuture-orchestration.html) | result 加 Completion 栈的结构、回调在哪个线程跑、thenCompose / thenCombine / allOf 与异常、默认池和超时不取消的坑、ThreadLocal 怎么带，回调线程先猜再看实验台 |
| 13 | [虚拟线程下一圈：什么时候用、pinning 的坑](https://archeu.github.io/study-notes/juc/virtual-threads-pinning.html) | 挂载卸载和载体线程、钉住的三种原因、trace 参数和 JFR 找钉住、ReentrantLock 修法与 JEP 491、什么时候不该用、和 J02 前八个知识点对照，载体线程甘特图实验台 |

## 网络

| # | 页面 | 内容 |
|---|------|------|
| 01 | [从输入 URL 到页面展示](https://archeu.github.io/study-notes/network/url-to-page.html) | 12 站全景、往返次数尺子、DNS 层级缓存、TCP + TLS 1.3 时序、慢启动、渲染阻塞、三次握手等设计取舍、Java 迷你浏览器实测（JDK 8 / 17 / 21）、往返计算器和 script 位置实验台 |
| 02 | [网络 IO 模型](https://archeu.github.io/study-notes/network/io-models.html) | 一万个连接要几个线程：五种 IO 模型的两段等待、连接便宜线程贵、Reactor 和 Tomcat NIO 连接器、事件循环为什么不能阻塞、HTTP 连接池和 keep-alive 等八个坑、BIO / NIO / 虚拟线程 1 万连接实测（JDK 17 / 21），keep-alive 连接分步演示 |
| 03 | [TCP：握手、挥手、TIME_WAIT 与粘包](https://archeu.github.io/study-notes/network/tcp-handshake-timewait-framing.html) | 连接是两端内核的两本账、三次握手为什么是三次、四次挥手和 CLOSE_WAIT、TIME_WAIT 为什么在先关的一方、字节流与长度前缀、Nagle × 延迟 ACK 的 40 ms、accept 队列，真实抓包逐段演示 |
| 04 | [Netty：EventLoop、Pipeline、ByteBuf](https://archeu.github.io/study-notes/network/netty-eventloop-pipeline-bytebuf.html) | EventLoop 终身绑定连接、Pipeline 入站出站方向、ByteBuf 双下标与引用计数、慢请求拖慢一个线程和漏 release 的实测、4.1→4.2 差异，EventLoop 阻塞实验台 |
| 05 | [RPC 原理：序列化、协议、服务发现、负载均衡](https://archeu.github.io/study-notes/network/rpc-serialization-discovery-lb.html) | 一次调用的八步、动态代理 Stub、自描述和约定结构的序列化、帧头与请求 id 多路复用、客户端发现与负载均衡、为什么这样设计，纯 JDK 迷你 RPC 实测（慢实例、坏实例、超时），负载均衡实验台 |
| 06 | [HTTP 客户端与连接池：超时怎么配](https://archeu.github.io/study-notes/network/http-client-pool-timeouts.html) | 一次调用的四段超时（拿连接、建连接、等响应、读响应）和总 deadline、读超时为什么不是总超时、池子满了在客户端排队、超时后对面照样做完、各客户端默认值对照，“哪个超时先到”实验台 |

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
| 03 | [new 一个对象的全过程：分配、对象头与内存布局](https://archeu.github.io/study-notes/jvm/jvm-object-new-layout.html) | new 的五步、TLAB 快速 / 慢速路径、mark word 与类指针、字段重排与对齐、压缩指针为什么卡在 32 GB、JOL 与关 TLAB 实测，对象布局实验台 |
| 04 | [GC 日志与调优：先定目标，再动参数](https://archeu.github.io/study-notes/jvm/jvm-gc-log-tuning.html) | 三个目标的取舍、一行日志怎么读、占比 / 最长停顿 / 回收后占用三样数、Parallel 固定分代 vs G1 自适应、交易靶场大促与泄漏实测、GC 日志体检台 |
| 05 | [类加载与双亲委派：SPI 为什么要打破它](https://archeu.github.io/study-notes/jvm/jvm-classloading.html) | 类的一生、三层加载器与 loadClass 源码、类的身份、为什么先问上级、SPI 借 TCCL 反向加载与 Tomcat 子优先、元空间泄漏实测，委派走一遍实验台 |
| 06 | [JIT、逃逸分析与常见的性能误区](https://archeu.github.io/study-notes/jvm/jvm-jit-escape.html) | 分层编译、内联和去虚化、逃逸分析与标量替换、去优化、热点 NPE 丢堆栈和预热等坑、六个性能误区，逃逸判定台 |
| 07 | [JVM 故障排查：OOM、频繁 Full GC、CPU 飙高](https://archeu.github.io/study-notes/jvm/jvm-troubleshooting.html) | 常见误判、先留现场再分两条路线、OOM 抛给了谁、Full GC 后降不降、shallow 和 retained、nid 对到一行、交易靶场三个雷实测（MAT、Humongous、JFR 分配和方法采样）、启动参数模板，排查练习台 |
| 08 | [容器里的 JVM：内存和 CPU 限制](https://archeu.github.io/study-notes/jvm/jvm-container.html) | cgroup 限额写在哪、JVM 读到后怎么定堆和 GC 和线程数、内核怎么杀进程和节流、堆按比例切加堆外逐块封顶、版本差异，容器内存预算台 |

## Java 基础

| # | 页面 | 内容 |
|---|------|------|
| 01 | [面向对象、接口与抽象类、泛型和类型擦除](https://archeu.github.io/study-notes/javase/oop-generics-erasure.html) | J01 第 1 个知识点：封装靠访问控制和防御性复制、多态靠运行时查方法表、接口与抽象类的分工和菱形问题、sealed 与 record、泛型从源码到运行的五步（编译期检查、擦除插 checkcast、Signature 留底、对象不知道元素类型）、为什么非擦除不可、桥方法与 TypeReference，JDK 17 实测与分步演示 |
| 02 | [常用集合怎么选：ArrayList、LinkedList、Set、Queue](https://archeu.github.io/study-notes/javase/collections-choose.html) | J01 第 2 个知识点：按“怎么找”选 List / Set / Map / Queue，ArrayList 扩容与头插、LinkedList 节点与缓存不友好、哈希与红黑树、ArrayDeque 环形数组、PriorityQueue 二叉堆与 DelayQueue，交易靶场订单簿，8 个场景先猜再看 JDK 17 实测 |
| 03 | [HashMap：哈希、扩容、树化](https://archeu.github.io/study-notes/javase/hashmap-internals.html) | J01 第 3 个知识点（过关题）：hashCode、扰动与 (n−1)&hash 定位，put 全过程 9 步，负载因子与翻倍扩容的高低位拆分，树化 8 / 6 / 64 与泊松分布，2 的幂对比 Hashtable 素数取模，并发写丢数据与 JDK 7 成环，put 模拟器与 JDK 17 反射实测 |
| 04 | [HashMap 的亲戚们：LinkedHashMap、WeakHashMap、ThreadLocalMap](https://archeu.github.io/study-notes/javase/hashmap-relatives.html) | HashMap 的下一圈：LinkedHashMap 的双向链表与三个钩子、访问顺序加 removeEldestEntry 做 LRU，WeakHashMap 的弱引用与 ReferenceQueue，ThreadLocalMap 挂在线程上、开放寻址与 0x61c88647，key 弱 value 强与线程池里的串号和内存泄漏，LRU 模拟器与 JDK 17 实测 |
| 05 | [Lambda、Stream、record、模式匹配：编译后变成了什么](https://archeu.github.io/study-notes/javase/lambda-stream-record.html) | J01 新特性的下一圈（机制）：invokedynamic 和四个引导方法，Lambda 的隐藏类与捕获，Stream 惰性流水线、Sink 链、短路与有状态操作，parallelStream 的公共池，record 的规范构造器与 ObjectMethods，sealed + switch 的 typeSwitch 与穷举检查，Stream 流水线分步演示，JDK 17 / 21 实测 |
| 06 | [异常、反射、注解与动态代理：Spring 下面那一层](https://archeu.github.io/study-notes/javase/exception-reflection-proxy.html) | J01 第 5 个知识点的下一圈（JDK 层）：受检与非受检、异常贵在填栈与 OmitStackTraceInFastThrow、try-with-resources 与 suppressed，Method.invoke 的 inflation 与 JDK 18 的 MethodHandle 实现、强封装，注解的保留策略与“注解对象也是代理”，生成的 $Proxy 类和异常表，手写事务 + 审计拦截器，代理调用分步演示，JDK 17 实测 |
| 07 | [IO 与 NIO 基础：字节怎么进来，怎么出去](https://archeu.github.io/study-notes/javase/io-nio-basics.html) | J01 第 6 个知识点的下一圈（API 与字节）：流的装饰器、字符集与乱码、缓冲为什么快（strace 数系统调用：一次一字节 200 万次对 263 次）、ByteBuffer 三指针与 flip / compact、堆内与直接缓冲、FileChannel.transferTo 与 sendfile、Files 工具，交易靶场导出导入，ByteBuffer 演示，JDK 17 实测 |
| 08 | [数据结构与算法：日常和面试够用的那部分](https://archeu.github.io/study-notes/javase/algorithms-everyday.html) | J01 最后一个知识点：先按数据量估复杂度，按最频繁的操作选结构，二分的不变式、Top K 小顶堆、滑动窗口限流、TimSort 与双轴快排及比较器约定，红黑树插入分步手推（和 TreeMap 反射实测逐步一致），面试题型地图，交易靶场四道题，JDK 17 实测 |
