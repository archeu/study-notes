# study-notes

图解学习笔记，大图少字。在线阅读：https://study.ainiya.de/

分两个板块：**AI Agent 工程师**是主线，按学习地图一站一站走；**Java 后端架构**是之前的全部笔记，作为主线的补给库，按技术栈分层（架构与性能、框架、存储与消息、Java 平台、网络）。首页有两个板块的入口、技术栈地图、最近新增和搜索。

配套代码在 [archeu/study-labs](https://github.com/archeu/study-labs)：页面上的快速入门、实测实验和练习，每页一个目录，克隆后用 IDE 打开就能跑（2026-11-09 之前的旧代码按原样收在 `legacy/`）。

# AI Agent 工程师（主线）

| # | 页面 | 内容 |
|---|------|------|
| 00 | [AI Agent 学习地图](https://study.ainiya.de/agent/roadmap.html) | 从 Java 后端到 AI Agent 工程师（v2.1，对照 26 份招聘要求修订，每站先看场景全景）：四个等级、十二站路线（99 个知识点、过关检验、补给站）、招聘要求统计图、贯穿项目值班助手、17 个 AI 概念的 Java 比方、每周 26 小时的节奏和 30 周时间表、已有 44 篇的去向，先定位搜索 |
| 01 | [全景：一个 FastAPI 请求的一生](https://study.ainiya.de/agent/pano-01-fastapi-request.html) | 站 01 的场景全景：一条 curl 进 FastAPI，经过 uv、uvicorn、路由、参数校验、端点协程、gather、事件循环、解析日志、响应模型、pytest 十站，每站挂上 Python 速成的知识点和 Java 对照；并发与串行耗时实测、order-04 超时、阻塞调用卡住事件循环，分步演示 |
| 02 | [uv 管环境和依赖（对照 Maven）](https://study.ainiya.de/agent/python-uv.html) | 站 01 第 1 个知识点：pyproject 写意图、uv.lock 钉死整棵依赖树、.venv 按锁算出来并从全局缓存硬链接；对照 Maven 的 classpath 和最近者优先，pip 与 uv 建环境耗时实测，九个坑、团队规范、CI 与 Docker 写法，uv run 先猜再跑实验台 |
| 03 | [全景：一句话怎么变成模型的回答](https://study.ainiya.de/agent/pano-02-prompt-to-answer.html) | 站 02 的场景全景：值班助手把 order-04 的 GC 日志交给模型，经过拼请求、分词、上下文窗口、查向量表、读完输入（注意力与 KV 缓存）、算概率、采样、逐 token 循环、停下、结算核对十站，每站挂上知识点和 Java 对照；本机小模型实测分词、候选概率、温度 0 和 1、输入长度与耗时、前缀缓存、幻觉，分步演示 |
| 04 | [语法对照：列表、字典、推导式、切片](https://study.ainiya.de/agent/python-collections.html) | 站 01 第 2 个知识点：对照 Java 讲列表和字典的内存布局、推导式和生成器、切片为什么复制而不是视图、8 个坑、推导式与生成器的速度和内存实测，切片实验台 |
| 05 | [函数是一等公民：闭包和装饰器](https://study.ainiya.de/agent/python-closure-decorator.html) | 站 01 第 3 个知识点：函数是对象、闭包的 cell 和迟绑定、装饰器就是 f = deco(f) 且在 import 时从下往上执行、monkeypatch 改的是哪个模块的名字；对照 Java lambda 和 Spring AOP 代理，8 个坑本机复现，装饰器实验台（顺序 × wraps × 同步异步，8 种组合 FastAPI 实测） |
| 06 | [类型标注和 Pydantic 数据模型](https://study.ainiya.de/agent/python-pydantic.html) | 站 01 第 4 个知识点：类型标注是运行时不检查的元数据、Pydantic 在类定义时编译出校验器、宽松和严格模式、FastAPI 入口 422 与出口 response_model 过滤；对照 Java 编译器、Jackson 和 Bean Validation，8 个坑本机复现，校验耗时实测，Pydantic 实验台（10 种输入 × 两种模式） |
| 07 | [asyncio：事件循环、async/await、并发请求](https://study.ainiya.de/agent/python-asyncio.html) | 站 01 第 5 个知识点：协程是能在 await 处暂停的函数、事件循环用一个线程加 epoll 同时等很多 socket、gather 与 TaskGroup 出错时的区别、超时和取消是协作式的；对照 Java 线程池、Netty 和虚拟线程，阻塞与 GIL 实测，8 个坑，“一个线程的时间线”实验台 |
| 08 | [FastAPI 写接口（对照 Spring MVC）](https://study.ainiya.de/agent/python-fastapi.html) | 站 01 第 6 个知识点：uvicorn、Starlette、FastAPI 三层分工，签名决定参数从路径、查询串、请求体还是依赖来，Depends、lifespan 共享连接池、def 端点的 40 线程上限；值班助手加假日志代理的真服务实测，7 个坑，“参数从哪来”实验台 |
| 09 | [pytest 写测试](https://study.ainiya.de/agent/python-pytest.html) | 站 01 第 7 个知识点：按名字收集、assert 改写、按参数名注入的 fixture 和作用域、dependency_overrides 加 MockTransport 不起外部服务测接口；对照 JUnit、Mockito、MockMvc，10 个测试先红后绿抓到一个真 bug，8 个坑，fixture 作用域实验台 |
| 10 | [用 AI 编程工具干活：Claude Code、Cursor](https://study.ainiya.de/agent/ai-coding-tools.html) | 站 01 第 8 个知识点（站末总结）：智能体循环、上下文窗口与 CLAUDE.md、checkpoint 和权限模式，复盘一次真实的修 bug，6 个在 ~/claude/oncall-helper 里亲手做的练习，“这件事交给 AI 吗”判断台 |
| 11 | [一次只写一个 token：下一个词预测](https://study.ainiya.de/agent/llm-next-token.html) | 手写生成循环逐 token 看前 3 名候选、训练就是猜下一个、结束符和 max_tokens、自回归为什么赢、开头一错一路错和不理结束符的实测，逐圈分步动画 |
| 12 | [token、分词和计费：同一段日志要花多少钱](https://study.ainiya.de/agent/llm-tokens-billing.html) | BPE 怎么合并出词表、中文和数字为什么费 token、字节回退、输入输出缓存批处理怎么计费、61 行 GC 日志原样和瘦身的 token 数实测，月成本计算器 |
| 13 | [上下文窗口：输入输出共用，越长越慢越贵](https://study.ainiya.de/agent/llm-context-window.html) | 输入输出共用一条定长带子、KV 缓存占内存、读输入和写输出为什么随长度变慢、关键一行埋在中间被漏、超长 400 和埋针实测，窗口装箱计算器 |
| 14 | [采样：temperature 和 top_p 改的是什么](https://study.ainiya.de/agent/llm-sampling.html) | 温度怎么调概率表的形状、top_p 怎么砍长尾、抽签和 seed、温度 0 为什么也会变（批处理和浮点）、温度 0/1 各 10 次和 4 个并发的实测、Claude 新模型不收采样参数，采样实验台 |
| 15 | [够用的数学：向量、点积和概率](https://study.ainiya.de/agent/llm-math-basics.html) | 补给页零基础：向量和意思近、点积和余弦、矩阵乘就是一堆点积、softmax 和先减最大值、概率连乘改 log 相加、五段 Python 手算，迷你注意力实验台 |
| 16 | [注意力和 KV 缓存（只讲到够用）](https://study.ainiya.de/agent/llm-attention-kv-cache.html) | Q/K/V 和因果遮罩、旧位置的 K/V 为什么能缓存、提示缓存为什么只认前缀、有无 KV 缓存写 20 个 token（0.8 秒对 128 秒）和时间戳放开头的实测，KV 缓存分步动画 |
| 17 | [推理模型和“思考”：用 token 换质量](https://study.ainiya.de/agent/llm-reasoning-thinking.html) | 一圈算力固定所以要打草稿、强化学习练出来的思考、思考按输出计费并算进 max_tokens、Claude 的 effort 和 display、Qwen3-0.6B 开关思考的数数实测（多 70～300 倍 token 仍答错），思考成本计算器 |
| 18 | [为什么会一本正经地编（幻觉）](https://study.ainiya.de/agent/llm-hallucination.html) | 幻觉的四个来源（只学像不像、必须挑一个、知识压在参数里、一错到底）、为什么先查再答能缓解、提示词温度和概率为什么都兜不住、三道题三种做法的实测，核对规则实验台 |
| 19 | [Embedding：文本变向量，意思近的靠得近](https://study.ainiya.de/agent/llm-embedding.html) | 向量表和句向量的区别、池化和归一化、对比学习、余弦只看排名、8 条工单 3 个提问的字重合对比余弦实测、否定句和指令前缀两个坑，相似工单检索实验台 |
| 20 | [怎么选模型：能力、价格、速度、开源闭源、国内外](https://study.ainiya.de/agent/llm-choose-model.html) | 按调用分类、先过硬约束（数据、合规、窗口、功能、延迟）再在自己的评测集上量质量成本速度、Claude 三档、开源和国内外的取舍、规则和两个小模型的告警分类实测，按调用分配模型的月成本计算器 |
| 21 | [全景：一次分诊调用的来回](https://study.ainiya.de/agent/pano-03-triage-call.html) | 站 03 场景全景：组装提示词、抽象层选模型、SDK 拼请求、HTTP 超时和重试、限流排队、缓存和生成、SSE 流回、收齐看 stop_reason、Pydantic 校验和重试、记录返回 10 站，官方 SDK 连本机模型的实测时间尺，分步演示 |
| 22 | [Messages API：角色、system、多轮其实是无状态的](https://study.ainiya.de/agent/api-messages.html) | 请求和响应的形状、system / user / assistant 三种角色、content 是块数组、stop_reason 和 usage、无状态和多轮重发、官方 SDK 连本机的原始 JSON 和带不带历史实测，多轮消息增长分步动画 |
| 23 | [提示词基本功：说清楚、给例子、用标签分隔](https://study.ainiya.de/agent/prompt-basics.html) | 说清字段取值和边界、示例为什么会被照抄、XML 标签分隔材料和防注入、不变的在前问题在后、四版提示词 8 条告警的对照实测、四个毛病和五个刻意练习，四版对照台 |
| 24 | [流式输出：SSE 一边生成一边推](https://study.ainiya.de/agent/api-streaming-sse.html) | Claude 流式事件的顺序和分层、SDK 怎么把事件拼回 Message、流式只让首字早到不省总时间、流到一半的 error 事件（状态码 200 且不自动重试）、首字时间和事件清点和中途出错的实测，首字与超时计算器 |
| 25 | [结构化输出：JSON Schema、Pydantic 校验、失败重试](https://study.ainiya.de/agent/api-structured-output.html) | 提示词、约束解码、Pydantic 校验加重试三层保险各管什么，约束解码怎么在采样时砍 token，带错误原因的有限次重试，schema 管不到的内容和业务规则，只靠提示词和约束解码各 100 次的实测（过关题 1），重试和失败数计算器 |
| 26 | [出错怎么办：429 限流、过载、超时，退避加抖动](https://study.ainiya.de/agent/api-errors-retry.html) | 429、529、超时各是什么、哪些该重试、退避解决压力而抖动解决同步、优先听 retry-after、只在一层重试和总截止时间、30 个客户端撞限流的五种策略实测和 SDK 自带重试的间隔，重试策略模拟器 |
| 27 | [省钱：提示词缓存和批处理](https://study.ainiya.de/agent/api-prompt-cache-batch.html) | 缓存的是前缀的 KV、tools → system → messages 的拼接顺序、写入 1.25 倍和命中 5%～10% 的账、5 分钟和 1 小时档、批处理五折和适用场景、命中前后的延迟和成本实测（过关题 2）以及前缀放请求号反而多花 23%，缓存和批处理月成本计算器 |
| 28 | [换模型只改一层：模型抽象层](https://study.ainiya.de/agent/llm-abstraction-layer.html) | 按任务配置模型和备用、适配器翻译两种接口格式、参数按模型能力过滤并留痕、错误分可重试和不可重试、统一常用的透传独有的、同一行业务代码跑三份配置的实测（含主服务挂了自动切备用），配置切换台 |
| 29 | [Java 版：用 Spring AI ChatClient 写同一个服务](https://study.ainiya.de/agent/spring-ai-chatclient.html) | Spring Boot 4.2 + Spring AI 2.1：starter 装配 ChatModel、ChatClient 链式调用、entity() 结构化、Flux 流式、spring.ai.model.chat 选提供方、只改配置换家的实测（接口换了，模型行为让 entity() 全部失败），extra-body 类型坑，两次运行对照台 |
| 30 | [全景：一次排障提问，agent 来回了几轮](https://study.ainiya.de/agent/pano-04-triage-agent.html) | 站 04 全景：值班助手 v1 不用框架手写 agent，本机实测 5 轮来回、并行工具、heap_dump 被闸门拦下，10 站对应 11 个知识点，分步演示 |
| 31 | [工具调用的一来一回：模型提议，你的代码执行](https://study.ainiya.de/agent/tool-use-roundtrip.html) | 站 04 第 1 个知识点：tool_use 和 tool_result 两种块、一来一回是两次请求四条消息、掀开盖子看模型原始写出的调用单、六个拼消息的坑，拼消息合规实验台 |
| 32 | [Agent 循环：调到不再要工具或到上限为止](https://study.ainiya.de/agent/agent-loop.html) | 站 04 第 2 个知识点：由 stop_reason 推动的状态机、messages 每轮整段重发总量随轮数平方增长、六种 stop_reason、实测 10 轮里打转 7 次和空回答，累计 token 与缓存账单实验台 |
| 33 | [停止条件：步数、预算、超时](https://study.ainiya.de/agent/agent-stop-conditions.html) | 站 04 第 3 个知识点：三种失控各用一道闸、闸在调模型之前查所以会超出一轮、两轮之间打断不了卡住的调用、撞闸后交出证据，假模型四场景 × 三道闸实验台 |
| 34 | [工具怎么设计：名字、描述、参数、精简的返回](https://study.ainiya.de/agent/tool-design.html) | 站 04 第 4 个知识点：工具四件套、给人的接口和给模型的工具约束不同、实测改说明书后时间参数修好而关键字仍对不上、原样 jstack 4.3 万 token 对摘要 152，说明书改法对照实验台 |
| 35 | [并行工具调用](https://study.ainiya.de/agent/parallel-tool-calls.html) | 站 04 第 5 个知识点：一轮多张调用单、只读的并发有副作用的串行、所有回执放一条消息、失败也要回，线程池与 asyncio.gather 实测，三种要法总耗时实验台 |
| 36 | [沙箱：只读优先、命令白名单、隔离执行](https://study.ainiya.de/agent/agent-sandbox.html) | 站 04 第 7 个知识点：参数是不可信输入、按可逆性分级、不过 shell 加命令和选项白名单加路径限定三道关、容器兜底，13 条命令含注入实测，命令停在哪一关实验台 |
| 37 | [危险操作先问人](https://study.ainiya.de/agent/human-approval.html) | 站 04 第 8 个知识点：按工具风险分 allow / ask / deny、审批卡片四要素、超时按拒绝、拒绝理由送回模型、审计日志，四个剧本实测，一晚 20 个告警三种策略实验台 |
| 38 | [工作流还是 Agent：五种常见模式怎么选](https://study.ainiya.de/agent/workflow-vs-agent.html) | 站 04 第 9 个知识点：谁决定下一步、五种工作流模式和 agent、四个问题检查单、路由在前 agent 兜底，同一告警工作流 81 秒对 agent 349 / 681 秒实测，选模式实验台 |
| 39 | [从需求到设计：拆专家 SOP、定成功指标](https://study.ainiya.de/agent/requirements-to-design.html) | 站 04 第 10 个知识点：问清需求、think aloud 拆专家 SOP、每步交给代码 / 工具 / 模型 / 人、五类成对指标，SOP 核对和全景真实运行打分实测，一步 SOP 变五样东西分步动画 |
| 40 | [先写 10 条评测用例，后面每站都跑](https://study.ainiya.de/agent/eval-first-cases.html) | 站 04 第 11 个知识点：固定现场加能用代码判的标准答案、边角用例占一半、宽进严出的判分，v1 实测 0 / 10 没看现场、只改工具说明后 2 / 10，评测还抓出判分器和工具的 bug，10 条结果逐条看的实验台 |
| 41 | [全景：第二天再问同一个服务](https://study.ainiya.de/agent/pano-05-next-day-memory.html) | 新会话从记忆表按团队召回 3 条病历、拼上下文、循环跑工具到 24.6K 时压缩旧工具结果、大日志交给子 agent、结论后抽取去重合并写回记忆、每晚遗忘、20 段回放评测，十站分步演示 |
| 42 | [上下文工程：放什么、放哪、放多少](https://study.ainiya.de/agent/context-engineering.html) | 五类内容按变化频率分层、预取一点加按需取、缓存只认前缀、每块定预算、工具结果截断，记忆放哪的缓存实测（命中 995 对 20）、拼装分步动画 |
| 43 | [上下文快满了：压缩、摘要、子任务隔离](https://study.ainiya.de/agent/context-compaction.html) | 滑动窗口为什么不行、清旧工具结果只留工具写的要点、交接摘要会丢细节会编数、子 agent 隔离大材料、清理与缓存的取舍、Claude context editing 参数，三招实测（11,905 → 2,802 / 1,606，子 agent +156）分步动画 |
| 44 | [记忆分几种：短期和长期，情景、语义、程序性](https://study.ainiya.de/agent/memory-types.html) | 短期记忆就是上下文、长期记忆要自己存取、情景追加 / 语义按 key 覆盖 / 程序性整组生效、记忆和 RAG 的区别、程序性记忆的三个去处，12 条记忆一锅端 vs 按类型取的实测（昨天那条排第 4）分步动画 |
| 45 | [记忆怎么写：抽取、去重、合并，新旧冲突听谁的](https://study.ainiya.de/agent/memory-write.html) | 抽取 / 去重 / 决定三步、同类同对象才比相似度、冲突按来源和时间、双时间轴旧值不删、hot path 与后台写、Mem0 与 Zep 对照，模型全权 vs 代码定边界两遍实测（4 条全错 vs 零损坏）分步动画 |
| 46 | [记忆怎么取：按相关性、时间、重要性召回](https://study.ainiya.de/agent/memory-retrieval.html) | 硬条件进 WHERE 不进分数、相关 / 新近 / 重要三个信号、min-max 归一后加权、Generative Agents 的做法、时间指代和取满 K 条的坑，25 条病历五种打分实测（昨天那条按相似度排第 12），调权重实验台 |
| 47 | [记忆怎么忘：衰减、过期，按用户隔离和隐私](https://study.ainiya.de/agent/memory-forget.html) | 过期 / 衰减归档 / 隐私隔离三件事分开做、记忆不可回源所以降权多于删除、写入脱敏加夜间扫描、行级安全、删除请求要删干净，SQLite 模拟 90 天四套策略实测（统一 TTL 删掉 P0），遗忘策略实验台 |
| 48 | [记忆好不好：该记的记住了吗，对任务有帮助吗](https://study.ainiya.de/agent/memory-eval.html) | 回放历史的用例写法（must / must_not / once）、记住 / 忘掉 / 冲突 / 隐私四类、记忆层 / 任务层 / 线上三层评测、用变异测试找盲区，21 个用例跑 v1 和 v2 的实测（8/20 vs 20/20）、覆盖矩阵、开关实验台 |
| 49 | [全景：一份运维手册从上传到被引用](https://study.ainiya.de/agent/pano-06-runbook-to-report.html) | 站 06 场景全景：手册 PDF 经同步、解析（含扫描页 OCR）、清洗切块、Embedding、pgvector 入库，再被 agent 检索、BM25 + 向量混合、重排，写进带引用的复盘报告；本机三次实跑的分段耗时和三种出错方式，11 站分步演示 |
| 50 | [RAG 流水线：切块、向量化、检索、重排、生成](https://study.ainiya.de/agent/rag-pipeline.html) | 闭卷和 RAG 的本机对照、两段路（索引和查询）分步动画、检索找的是最像不是最对、双塔粗筛加交叉编码精排、五个实测的坑、30 题命中率随 k 变化的实验台 |
| 51 | [文档解析：PDF、Word、表格、扫描件](https://study.ainiya.de/agent/doc-parsing.html) | PDF 内容流原样拆解、版面分析分步动画、表格两种取字对照、OCR 四步、Word 的 XML 结构、PDF 为什么这样设计、六个实测的坑、扫描分辨率和倾斜实验台 |
| 52 | [清洗、切块策略和元数据](https://study.ainiya.de/agent/chunking-metadata.html) | 三类噪声和清洗规则、按标题切块分步动画、元数据的三种用途、为什么片要小而完整、7 种做法 × 30 题的本机对比、六个实测的坑、切法对比实验台 |
| 53 | [向量检索和 HNSW 索引](https://study.ainiya.de/agent/vector-hnsw.html) | 暴力扫描为什么不行、四种少看的思路、HNSW 的近邻图、分层和 ef、三层小图手推分步动画、pgvector 5 万条实测（HNSW、IVFFlat、过滤和 iterative_scan）、六个坑、召回率与延迟实验台 |
| 54 | [混合检索：关键词 BM25 加向量，再重排](https://study.ainiya.de/agent/hybrid-search.html) | 两路盲区对照、BM25 打分逐词拆解（饱和、IDF、长度打折）、RRF 只看名次的算例、重排漏斗分步动画、6 种办法 × 30 题本机实测、六个坑、RRF 的 k 和权重实验台 |
| 55 | [评测：检索命中率和答案忠实度](https://study.ainiya.de/agent/rag-eval.html) | 分两段评、错因交叉表、hit@k 和 MRR、忠实不等于正确、判官要先和人工对、30 题的误差有多大、33 题本机实测（含 3 道库外题和人工标注）、五个刻意练习、关键词判官阈值实验台 |
| 56 | [RAG 优化：查询改写、元数据过滤、父子块](https://study.ainiya.de/agent/rag-optimize.html) | 三种病三种药、版本和日期过滤实测、父子块分步动画、1.7B 模型改写和 HyDE 为什么帮倒忙、多路查询、先规则后模型的设计、五个坑、两种做法逐题对比实验台 |
| 57 | [知识库运维：增量同步、权限、版本](https://study.ainiya.de/agent/kb-ops.html) | 一天 8 次变更的时间轴、全量重建的代价、五种同步方式、三层身份（文件、文档、片）、三种状态、权限一列、pgvector 实测加新手册 1.9 秒可查、六个坑、增量和全量对比实验台 |
| 58 | [让 agent 自己决定查什么（Agentic RAG）](https://study.ainiya.de/agent/agentic-rag.html) | 多跳问题、原话查一次的实测、六种流派和控制权光谱、推演与 1.7B 实测对照的分步动画、代码兜底和工具说明书、4 题 × 6 种做法本机实测、五个误用、逐题对照实验台 |
| 59 | [内容生成：带引用的长文报告](https://study.ainiya.de/agent/report-generation.html) | 点回原文是什么样、一次写完的实测、五种写法、提纲到渲染的六步分步动画、全局编号、代码算事实和规则、逐句回查的边界、三份报告逐句人工核对、六个坑、点开编号看原文的报告查看器 |
| 60 | [全景：Claude Code 调用你的 MCP 工具](https://study.ainiya.de/agent/pano-07-mcp-call.html) | 站 07 场景全景：Claude Code 读配置、用 stdio 拉起 Python 服务端、用 HTTP + OAuth 连远程服务端，server/discover 协商（新协议无握手，老服务端回退 initialize），tools/list、工具说明进上下文、按需加载 Skill、权限把关、tools/call 执行、tool_result 回模型；本机抓的真实报文和对数时间尺，10 站分步演示 |
| 61 | [MCP 的三方：主机、客户端、服务端](https://study.ainiya.de/agent/mcp-architecture.html) | M×N 变 M+N、站 04 内嵌工具的痛点、主机 / 客户端 / 服务端各管什么、JSON-RPC 三种消息按 id 配对、2026-07-28 去掉握手改成每个请求自带版本（老服务端探测回退 initialize）、四个坑，一次连接的分步时序图 |
| 62 | [三种能力：工具、资源、提示词模板](https://study.ainiya.de/agent/mcp-primitives.html) | 按“谁决定什么时候用”分三种：模型控制的工具、应用控制的资源、用户控制的提示词模板；全做成工具的代价、工具定义五件套和三种出错、资源模板、模板展开、annotations 只是提示、SDK 与规范对不上的两处，“该做成哪一种”实验台 |
| 63 | [两种传输：stdio 和 Streamable HTTP](https://study.ainiya.de/agent/mcp-transports.html) | stdio 一行一条走管道、stdout 只许走协议，Streamable HTTP 一个 POST 端点、必带请求头、JSON 或 SSE；2024 年 HTTP+SSE 为什么被换掉、请求头为什么要把 body 再写一遍；curl 实测 403 / 400 -32020 / -32022 / 202，stdio 和 HTTP 各 100 次调用的计时，一次 tools/call 过关的分步图 |
| 64 | [写 MCP 服务端：Python 和 Java 各一个](https://study.ainiya.de/agent/mcp-server-build.html) | Python 用 MCPServer + 装饰器写 oncall（lifespan、Context、ToolError、内存测试），Java 用 Spring AI 2.1.0 的 @McpTool 写 tickets；签名和注释怎么变成工具定义、一次调用在 SDK 里的六步；实测 -parameters、异常透出、协议年代只能选一个、多实例密钥四个坑，两个服务端被 Python SDK 和 Claude Code 连通 |
| 65 | [远程 MCP 的鉴权（OAuth）](https://study.ainiya.de/agent/mcp-oauth.html) | MCP 服务端当 OAuth 资源服务器：401 指路、RFC 9728 / 8414 发现授权服务器、注册、授权码 + PKCE + resource、令牌绑定受众、scope 按需升级、禁止透传；本机用 SDK 搭授权服务器走完 13 个 HTTP 来回，实测 issuer 斜杠、注册 scope、受众校验等五个坑，分步时序图 |
| 66 | [MCP 的安全：不可信服务端、工具描述投毒、最小权限](https://study.ainiya.de/agent/mcp-security.html) | 代码层、文字层、权限层三层风险，2025 年三次公开演示（工具描述投毒、rug pull、公开 issue 间接注入），审 / 钉住 / 扫描 / 隔离 / 权限闸 / 拆三件套各挡什么，本机实测体检脚本抓住 rug pull，Claude Code 的最小权限配置，“致命三件套”检查器 |
| 67 | [Agent Skills：按需加载的说明书](https://study.ainiya.de/agent/agent-skills.html) | 说明书放哪：CLAUDE.md、提示词模板、RAG、MCP 工具各缺什么；SKILL.md 格式、描述就是触发条件、三层按需加载、Skill 和 MCP 的分工；把值班 SOP 写成 oncall-triage（带脚本和参考文件），本机实测每层进上下文的字数和官方校验工具，三层分步图 |
| 68 | [全景：一个告警进来以后](https://study.ainiya.de/agent/pano-08-alert-to-ticket.html) | 站 08 全景：n8n 接告警、LangGraph 起图、主 agent 分诊、Send 并行派三个子 agent、检查点、interrupt 等人批准、幂等键建工单、审计，11 站分步演示和时间尺 |
| 69 | [框架替你做了什么、藏了什么](https://study.ainiya.de/agent/framework-what-it-hides.html) | 站 08 下钻 1：手写循环和 LangGraph 逐项对照、控制反转、五个藏起来的默认值（recursion_limit 10007、durability、重试、超时、线程池）、恢复为什么以节点为单位，一次 invoke 的分步动画 |

# Java 后端架构（补给库）

| # | 页面 | 内容 |
|---|------|------|
| 00 | [Java 后端架构学习地图](https://study.ainiya.de/java/roadmap.html) | 从高级工程师到架构师（每站先看场景全景，J04 用“从输入 URL 到页面展示”）：三个等级、十六站路线（117 个知识点，J06 含 PostgreSQL 对照，J11 含 TiDB、OceanBase、GoldenDB、过关检验、待做页）、25 份招聘要求统计和已有页面的缺口、交易靶场贯穿、两段式安排（AI 主线期间按需补，走完后约 15 周系统学）、版本基线，先定位搜索 |
| 01 | [全景：一个订单对象的一生](https://study.ainiya.de/java/pano-j01-order-object-life.html) | J01 的场景全景：用户 1024 下单 2 件 88 号商品，一个 Order 经过 Tomcat 收字节、Jackson 反序列化成 record、Spring 代理开事务、HashMap 查商品、new 实体与泛型擦除、Stream 和模式匹配算价、扣库存抛异常回滚、放进集合、DelayQueue、序列化写回、留在堆里十一站，每站挂上 J01 知识点；本机 Spring Boot 实测每站类名、桶下标、冷热耗时和存活对象数，分步演示 |
| 02 | [全景：一个下单请求在线程池里](https://study.ainiya.de/java/pano-j02-order-in-threadpool.html) | J02 的场景全景：1000 人抢 100 件 88 号键盘，一个请求经过 Tomcat Acceptor 和 Poller、exec 线程池、ThreadLocal 绑用户、读库存、写回撞车超卖，再分三种修法（synchronized、CAS、数据库条件更新），最后进 ConcurrentHashMap、CompletableFuture 异步通知、清 ThreadLocal 回池十一站，每站挂上 J02 知识点；本机 Spring Boot 实测五种写法的超卖件数、BLOCKED 线程数和虚拟线程，分步演示 |
| 03 | [全景：一个对象从 new 到被回收](https://study.ainiya.de/java/pano-j03-object-new-to-gc.html) | J03 JVM 与调优的场景全景：类加载、JIT 与逃逸分析、TLAB 分配、大对象、Young GC、晋升、并发标记与 Mixed GC、泄漏到 Full GC、OOM 排查、容器内存十站，附实测 GC 日志，分步演示 |
| 04 | [全景：订单服务调库存服务的一次 RPC](https://study.ainiya.de/java/pano-j04-order-calls-inventory.html) | J04 场景全景：Stub、服务发现与负载均衡、长连接、protobuf、HTTP/2 帧、Netty EventLoop、TCP、服务端 Reactor、业务线程池、deadline 十站，gRPC 对 HTTP/1.1 的延迟和连接数实测，分步演示 |
| 05 | [全景：一个请求穿过 Spring](https://study.ainiya.de/java/pano-j05-request-through-spring.html) | J05 场景全景：启动装配、Tomcat、Security 过滤器链、DispatcherServlet、参数解析、AOP 代理、事务拦截器、Mapper 代理、Executor 与插件、提交后事件、回程十一站，SQL 发出时 131 层调用栈和分段耗时实测（BCrypt 占 82 ms、自调用不回滚），分步演示 |
| 06 | [全景：一条 UPDATE 从应用到磁盘](https://study.ainiya.de/java/pano-j06-update-to-disk.html) | J06 场景全景：借连接、发 SQL、连接线程、解析优化、B+ 树找页、行锁、undo、改页写 redo、两阶段提交、回 OK、从库回放、刷脏页十二站，MySQL 8.4 一主一从实测（冷读 3 页、提交等落盘 3 ms、提交 120 秒后页仍是脏的），分步演示 |
| 07 | [全景：一次商品详情查询](https://study.ainiya.de/java/pano-j07-product-detail-cache.html) | J07 场景全景：查本地、发 GET、主线程查字典、布隆过滤器、重建锁、查库、回填加解锁、放本地、改价提交、删 Redis、广播失效、后台落盘淘汰十二站，Redis 8.10 + Caffeine + MySQL 8.4 实测（本地命中 4 µs、Redis 往返 279 µs 而服务端只要 2 µs、击穿时查库 1～26 次加锁后 1 次、改价后 11～26 ms 跟上），分步演示 |
| 08 | [全景：一条订单消息的一生](https://study.ainiya.de/java/pano-j08-order-event-life.html) | J08 场景全景：写 outbox、选分区、攒批发出、追加写、副本复制、回 ACK、三组拉取、处理去重、提交位点、心跳重平衡、段与保留十一站，Kafka 4.4 三 broker 实测（ACK 12～19 ms、三组 12～20 ms 收到、停两个副本写入被拒、提交前崩溃重投一次靠去重表挡住），分步演示 |
| 09 | [全景：一次下单跨三个库](https://study.ainiya.de/java/pano-j09-order-across-three-dbs.html) | J09 场景全景：订单 9527 用 Seata TCC 在订单、库存、券三库各写一笔，幂等键、号段、TC Raft 决议、Confirm 重试、outbox 加锁投递、中途 kill -9 的超时回滚与空回滚、对账兜底十一站，三库状态表，联动分步演示 |
| 10 | [全景：拆成微服务后的一次下单](https://study.ainiya.de/java/pano-j10-order-through-microservices.html) | J10 场景全景：订单 9527 穿过网关鉴权、限流、灰度路由，Nacos 推来的超时配置，OpenFeign 串行调商品、券、库存，inventory-2 卡住却仍“健康”，Sentinel 慢调用熔断与降级、摘流量后 35 秒缓存才恢复，每一跳的超时预算表，分步演示 |
| 11 | [全景：订单表从一张到八张](https://study.ainiya.de/java/pano-j11-order-table-sharding.html) | J11 场景全景：t_order 1.2 亿行按 user_id 拆成 2 库 8 表，库表余数为什么要同源，双写、分批搬运、校验到差 0、先切读再切写的回滚开关，ShardingSphere 改写路由，老订单号没有基因，跨片分页放大，按商家查交给 ES，binlog → Canal → Kafka 同步，换 TiDB / OceanBase / GoldenDB 这另一条路，分步演示 |
| 12 | [全景：10 万人抢 1000 张券的那一秒](https://study.ainiya.de/java/pano-j12-coupon-rush.html) | J12 场景全景：算账和全链路压测定出 8 台、限流 1 万/秒，30 万次点击经 App 置灰、CDN 静态化、网关令牌桶、售罄标记、Redis Lua 预扣、RocketMQ 异步落库削到 1000 行，条件更新兜底防超发，Redis 切主库存回涨、机房断电同城双活切流，对数漏斗图，分步演示 |
| 13 | [全景：凌晨三点，告警响了](https://study.ainiya.de/java/pano-j13-late-night-alert.html) | J13 场景全景：对账任务在事务里等支付渠道 30 秒，占满 order-3 连接池，下单 1/3 失败；Micrometer 指标、JSON 日志、OTel 链路三路埋点，Prometheus 规则 for 5m 加 Alertmanager 打电话，接警定级、大盘按实例和连接池缩范围、慢 trace 没有子 span、按 trace_id 查日志、问变更、Arthas 看线程和耗时、Nacos 开关止血、复盘五问和改进项，30 分钟时间尺，分步演示 |
| 14 | [全景：一次发布，从合并到回滚](https://study.ainiya.de/java/pano-j14-one-release.html) | J14 场景全景：order-svc 1.8.3 → 1.8.4，合并请求顺手带进 -Xmx1g；GitHub Actions 跑 mvn verify，多阶段构建按层拆 jar，Harbor 只推变了的那层，Argo CD 同步部署仓库，Deployment 新 ReplicaSet maxSurge 1 / maxUnavailable 0，调度按 requests，JVM 按 cgroup 定堆，startup 和 readiness 探针，EndpointSlice 切流量、preStop 加 SIGTERM 优雅退出，晚高峰 HPA 4 → 6 后 OOMKilled 137，git revert 回滚，7 分钟时间尺和滚动阶梯，分步演示 |
| 15 | [全景：一个需求从一句话到方案评审](https://study.ainiya.de/java/pano-j15-requirement-to-review.html) | J15 场景全景：运营一句“满 300 减 40 要能和券叠加”，先满减还是先打折差 4 块钱；追问出 6 个答案，落成规则表、算例和事件，看清 420 行的 calcPrice，按“优惠”一词的两种意思划出订单域和营销域，算价放进券服务的独立模块而不新建服务，3 条 ADR 各带被放弃的方案，策略加责任链加防腐层，8 页方案过 45 分钟评审，再先搬后改分小 PR 落地；十站分步演示和五个工作日的时间尺 |

## Spring

| # | 页面 | 内容 |
|---|------|------|
| 01 | [Spring MVC 请求关卡](https://study.ainiya.de/spring/spring-web-gates.html) | Filter、Interceptor、WebMvcConfigurer 的区别、生命周期和用途 |
| 02 | [Spring AOP 与事务](https://study.ainiya.de/spring/spring-aop-tx.html) | 代理、切面、通知，@Transactional 的提交回滚、传播、隔离和失效场景 |
| 03 | [Spring Boot 自动配置](https://study.ainiya.de/spring/spring-boot-autoconfig.html) | starter、自动配置清单、条件注解，启动时序和自定义 starter |
| 04 | [Bean 生命周期与循环依赖](https://study.ainiya.de/spring/spring-bean-lifecycle.html) | 十四站生命周期、回调顺序、作用域，三级缓存怎么解循环依赖 |
| 05 | [Spring Security 认证与授权](https://study.ainiya.de/spring/spring-security.html) | 过滤器链、核验台、工牌和门禁，401 和 403 从哪来，Security 5 和 6 的写法差别 |
| 06 | [Spring MVC 请求处理流程](https://study.ainiya.de/spring/spring-mvc-flow.html) | DispatcherServlet 的 doDispatch 八步，参数解析、页面和 JSON 两种返回、异常善后 |
| 07 | [Spring Boot 启动流程](https://study.ainiya.de/spring/spring-boot-startup.html) | run() 的四段路、refresh 十二步、Tomcat 什么时候开端口，事件顺序、扩展点和启动失败 |
| 08 | [Spring 事件机制](https://study.ainiya.de/spring/spring-events.html) | 发布者、广播站、监听器，同步、@Async、@TransactionalEventListener 怎么选，事件实验台 |
| 09 | [Spring IoC 与依赖注入](https://study.ainiya.de/spring/spring-ioc-di.html) | 容器里有什么、图纸从哪来、三种注入写法，同类型多个 Bean 时怎么选的注入裁判 |
| 10 | [Spring AOP 代理原理](https://study.ainiya.de/spring/spring-aop-proxy.html) | 替身什么时候换上、JDK 代理和 CGLIB、调用怎样穿过拦截器链，替身管不到的地方 |
| 11 | [Spring @Async 与线程池](https://study.ainiya.de/spring/spring-async-pool.html) | @Async 背后的派单员、用哪个线程池、四步规则和拒绝策略，线程池模拟器 |
| 12 | [代理是哪一刻换进容器的：Bean 生命周期下一圈](https://study.ainiya.de/spring/spring-bean-proxy-swap.html) | refresh 三段和 BPP 三组登记、代理在初始化最后一步换进去、@PostConstruct / 循环依赖 / BPP 提前建三条漏口、@Async 环的 raw version 和 Spring 6.2 的变化，九个场景的先猜再跑实验台 |
| 13 | [249 个 bean 是谁建的：Boot 自动配置与启动下一圈](https://study.ainiya.de/spring/spring-boot-bean-ledger.html) | 两道筛子（158→43→35）、249 个 bean 的账本、全景各站对象出自哪张图纸、“你没写我才写”的让位规矩、3.8 s 启动时间账、六个实测坑，七场景先猜再跑实验台 |
| 14 | [代理里那十几层在干什么：AOP 与代理下一圈](https://study.ainiya.de/spring/spring-aop-chain.html) | 调用栈 11 层逐层拆开、启动时链怎么过筛加头排序、@Async 插到第 0 位、下标走链与一个代理一条链的设计、计时漏算提交和重试切面在事务里等四个坑、每层开销粗测与 6.1/6.2、JDK 17/21 差异，排链先猜再跑实验台 |
| 15 | [付款失败，流水要不要一起撕：事务传播、隔离与失效下一圈](https://study.ainiya.de/spring/spring-tx-propagation.html) | 进门先问线程上有没有事务、三种传播在连接上的样子、提交六步和提交后写库、REQUIRES_NEW 借空连接池和自锁、隔离和超时何时生效、Spring 6.0～7.0 护栏，3×4 付款组合先猜再跑实验台 |
| 16 | [一个 400 进了两次 DispatcherServlet](https://study.ainiya.de/spring/spring-mvc-dispatch.html) | Spring MVC 请求处理下一圈：分派类型与 /error 再分派、过滤器按分派登记的两层开关、拦截器调两次、Boot 3 公开接口出错变 401、过滤器重复注册、冷热请求时间账，八个场景的分派演示 |
| 17 | [付款一次算一遍密码：Spring Security 认证与授权下一圈](https://study.ainiya.de/spring/spring-security-token.html) | BCrypt 为什么故意慢和 cost 实测、登录一次换会话或 JWT、JWT 怎么验（签名、60 秒偏差、SCOPE_ 前缀）、@PreAuthorize 按数据授权、显式保存、会话固定、登出撤销六个坑，凭证实验台 |
| 18 | [改个版本号，付款就 400 了：Spring Boot 3 到 4、Jakarta 与 Jackson 3 升级](https://study.ainiya.de/spring/spring-boot4-upgrade.html) | 编译器看得见的改名和看不见的默认值、Jackson 3 怎么换掉第 5 站、MyBatis 旧 starter 为何找不到 Mapper、六个坑和五个练习，四种构建 × 六个付款请求的先猜再跑实验台 |
| 19 | [测试全绿，付款照样没回滚：JUnit 5、Mockito 与 Testcontainers](https://study.ainiya.de/spring/spring-testing.html) | JUnit 5 平台和扩展、Mockito 的答案表和录像带、Web / MyBatis 切片和上下文缓存、Testcontainers 起真 MySQL、三颗事务雷只有真库整链测试抓得到、测试类加 @Transactional 全部失真、Boot 4 测试依赖变化，测试层 × 写法实验台 |

## MyBatis

| # | 页面 | 内容 |
|---|------|------|
| 01 | [MyBatis 执行流程](https://study.ainiya.de/mybatis/mybatis-flow.html) | 启动时编好 SQL 手册，一次调用经过 MapperProxy、SqlSession、Executor 和 JDBC，两级缓存、#{} 与 ${}、插件 |
| 02 | [MyBatis 与 Spring 事务](https://study.ainiya.de/mybatis/mybatis-spring-tx.html) | 同一个 DataSource、线程上的储物柜、SqlSessionTemplate 复用会话，谁来提交，五个剧情看回滚和坑 |
| 03 | [MyBatis 插件与分页](https://study.ainiya.de/mybatis/mybatis-plugin-page.html) | 四个能拦的对象、Plugin.wrap 套娃和登记顺序，PageHelper 和 MyBatis-Plus 怎么分页，深分页 |
| 04 | [MyBatis 缓存与 Caffeine](https://study.ainiya.de/mybatis/mybatis-cache.html) | 一级、二级缓存怎么存怎么清，五个剧情看旧数据，和 Caffeine 逐项对比，LRU 与 W-TinyLFU 命中率 |
| 05 | [MyBatis-Plus 原理](https://study.ainiya.de/mybatis/mybatis-plus.html) | 启动时注入 SQL、Wrapper 怎么变成 SQL、自动填充和雪花 ID、插件总管和顺序，saveBatch 怎么批量 |
| 06 | [100 笔订单发出 101 条 SQL：MyBatis 结果映射、N+1 与流式查询](https://study.ainiya.de/mybatis/mybatis-result-mapping.html) | JOIN 的行怎么靠 <id> 折叠成对象、嵌套查询的 N+1、懒加载代理在事务外每次借连接、明细字段全 null、JOIN 后分页少订单、Cursor 离不开事务和驱动 fetchSize、分页导出被一级缓存拽住，8 组交易靶场实测和逐行折叠演示 |

## 数据库

| # | 页面 | 内容 |
|---|------|------|
| 01 | [连接池与事务性能](https://study.ainiya.de/database/db-pool-tx-perf.html) | 为什么建连接贵、池子开多大、事务怎么吃掉连接、提交落盘和长事务、驱动参数，连接池模拟器 |
| 02 | [MySQL MVCC 与锁](https://study.ainiya.de/database/mysql-mvcc-lock.html) | 隐藏列和版本链、Read View 怎么判断看得见、快照读和当前读、四种行锁和死锁，MVCC 实验台和锁地图 |
| 03 | [HikariCP ConcurrentBag 源码](https://study.ainiya.de/database/hikari-concurrentbag.html) | 口袋、货架、递交窗口和 state CAS、为什么借连接不加锁却不保证先来先得、先改 state 再看 waiters、逐行读 borrow / requite、各版本差异，线程调度实验台 |
| 04 | [100 万行里找 9527，只读了 3 页：索引与 B+ 树](https://study.ainiya.de/database/mysql-index-bplustree.html) | 页和 B+ 树为什么只有 3 层、页目录二分、聚簇索引和二级索引、回表与覆盖索引、联合索引最左前缀、为什么二级索引存主键，读 .ibd 数树形和拿页次数实测，查询走法演示 |
| 05 | [明明有索引，它偏不走：执行计划与 SQL 调优](https://study.ainiya.de/database/mysql-explain-tuning.html) | 慢查询日志与按指纹汇总、EXPLAIN 各列、EXPLAIN ANALYZE 对估算、代价模型与回表分界点实测、索引失效六种写法、深分页与游标分页，16 种写法先猜再看实验台 |
| 06 | [两次付款同时到，第二次改了 0 行：事务、MVCC 与锁（下一圈）](https://study.ainiya.de/database/mysql-lock-wait-deadlock.html) | 快照读与当前读、等锁醒来后重新判断 WHERE、三种 WHERE 在 RR / RC 下锁了多少行、1205 只回滚一条语句、死锁日志怎么读，连点两次付款实验台 |
| 07 | [commit 返回了，数据页还是旧的：redo、undo、binlog 与两阶段提交](https://study.ainiya.de/database/mysql-redo-undo-binlog.html) | WAL 与检查点、undo 版本链与 purge、binlog 与 redo 的分工、两阶段提交和崩溃恢复规则、提交途中 kill -9 三次实测、redo 容量与长事务实测，崩溃点实验台 |
| 08 | [付完款跳回订单页，还是待付款：主从复制、读写分离与复制延迟](https://study.ainiya.de/database/mysql-replication-lag.html) | 三个线程两份日志、GTID、延迟拆成传排队回放、大事务与心跳曲线、从库被写停在 1032、读写分离三种写后读，路由实验台 |
| 09 | [orders 加一列，支付接口全卡住了：表结构设计与大表变更（Online DDL）](https://study.ainiya.de/database/mysql-online-ddl.html) | 建表时每个类型的改表代价、INSTANT / INPLACE / COPY 三种算法、元数据锁排队、DDL 到从库再做一遍、gh-ost 影子表对照，一边付款一边改表的实测，改表计划台 |
| 10 | [池子从 10 开到 50，付款一点没快：连接池与事务性能（下一圈）](https://study.ainiya.de/database/db-pool-tx-perf-hot-row.html) | 热点行吞吐 ≈ 1 ÷ 持锁时间、队伍从 HikariCP 挪进 InnoDB、组提交为什么在热点行上凑不成组、8 组靶场实测和池子 1～64 曲线，三开关实验台 |
| 11 | [换上 8.4，付款服务连不上库了：MySQL 8.0 升级 8.4 LTS](https://study.ainiya.de/database/mysql-84-upgrade.html) | 8.0 停更与 LTS 发布模型、启动时自动升级且单向、先升从库再切换、账号插件 / MASTER-SLAVE 语法 / 默认值 / 外键四类变化、caching_sha2_password 缓存、交易靶场全程实测，连接实验台 |
| 12 | [订单表一行没加，PG 里却胖了一倍：PostgreSQL 的多版本、VACUUM、索引类型和 JSONB](https://study.ainiya.de/database/pg-mvcc-vacuum-jsonb.html) | PG 不原地改行、旧版本留在表里、可见性与回滚、页内修剪 / VACUUM / autovacuum / VACUUM FULL、长事务挡住清理、HOT 与 fillfactor、xid 冻结、B-tree / BRIN / GIN / 部分索引与表达式索引、JSONB 与 GIN，全部在 PG 18.7 上实测，堆表实验台 |
| 13 | [工单库要加“找相似故障”：MySQL 还是 PostgreSQL，pgvector 凭什么](https://study.ainiya.de/database/mysql-vs-pg-pgvector.html) | MySQL 和 PG 逐项对比、向量放哪的五种方案和选择规则、PG 扩展的四个插槽（类型、运算符、运算符类、索引访问方法）、带过滤查询的执行路径、为什么 MySQL 社区版做不出向量索引、本机实测带条件少行和三种补法，过滤 HNSW 实验台 |
| 14 | [订单表拆成 8 张：分库分表与 ShardingSphere](https://study.ainiya.de/database/sharding-shardingsphere.html) | J11 知识点 1：2000 万口诀从哪来（B+ 树层数估算）、真正逼着拆的是写入和运维时间、便宜的招各解决什么、垂直 / 单库分表 / 分库分表、取模 / 范围 / 映射、分片键三条标准、库表同源（实测 2500/0 vs 1250）、ShardingSphere-JDBC 5.5.3 五步与 12 条 SQL 的真实改写、5.5.3 依赖拆包的四种报错，分片键试验台 |
| 15 | [9527 在哪张表：分片以后的跨片查询、分页与全局表](https://study.ainiya.de/database/sharding-cross-shard-query.html) | J11 知识点 2：四种查询各碰几张表、订单号基因的复合分片算法与老单号广播、跨片深分页的全局视野改写和内存归并（实测 offset 100000 时 2.4 s / 2.7 GB，游标 23 ms）、LIMIT 0,1020 起 MySQL 改走 filesort、AVG 与 GROUP BY 改写、绑定表 32 → 8 条、唯一索引只管一张表，跨片分页代价计算器 |
| 16 | [1.2 亿行搬进 8 张表，App 不停：不停机数据迁移](https://study.ainiya.de/database/online-data-migration.html) | J11 知识点 3：停机迁移为什么回不去、应用双写 / binlog 增量 / ShardingSphere 迁移任务、七个阶段谁是主怎么退、搬运覆盖和乱序两种竞态、版本保护 + INSERT IGNORE、分块 BIT_XOR(CRC32) 校验再逐行修、影子读与灰度切读、反向双写，带流量的迁移演练（naive 倒退 95 行、safe 0 行，修复后差 0），回滚推演台 |
| 17 | [不自己拆，换个数据库：TiDB、OceanBase、GoldenDB 替你做了什么](https://study.ainiya.de/database/distributed-db-tidb-oceanbase.html) | J11 知识点 6：全景第 2～8 站在分布式数据库里由谁做、自己拆的几处长期痛点、TiDB 计算存储分离 / OceanBase 一体化 Paxos / GoldenDB 分片 + GTM 三种架构、Region 与 PD 调度、Raft 多数派提交与 RPO = 0、TSO + Percolator 两阶段提交、计算下推，TiDB 8.5.8 小集群实测（杀 follower 无感、杀 leader 写入停 13.9 s 且 0 失败），多数派计算器 |
| 18 | [代码没改，行为变了：从 MySQL 换到 TiDB 要注意的四件事](https://study.ainiya.de/database/mysql-to-tidb-pitfalls.html) | J11 知识点 7：自增 ID 每台 server 各缓存一段（实测 1/30001、重启跳到 60001，AUTO_ID_CACHE = 1 连续）、按主键范围分片的写热点（实测 2 万行全在 1 个 Region vs AUTO_RANDOM 分到 8 个）、事务大小上限与单行 6 MiB（8004 / 8025）及 Pipelined DML、RR 实为快照隔离没有间隙锁（MySQL 挡 3 s 超时 vs TiDB 13 ms 插入成功），迁移前排查清单，主键选型台 |

## 性能

| # | 页面 | 内容 |
|---|------|------|
| 01 | [系统压测](https://study.ainiya.de/perf/load-testing.html) | 看哪五个数、六种压测、吞吐为什么会到顶、八类常见瓶颈的原理和解法、方案优劣和工具对比，压测曲线和瓶颈实验台 |
| 02 | [响应时间为什么越压越长](https://study.ainiya.de/perf/response-time-queueing.html) | 六步排查：RT 的账单、四问排查路线、一串窗口和浴缸、开环积压与出口变窄、超时重试的反馈环、排队还是拒绝，四个本机实验和排队实验台 |
| 03 | [压出来的才算数：全链路压测与容量规划](https://study.ainiya.de/perf/full-link-load-test.html) | J12 第 5 个知识点（系统压测的下一圈）：测试环境压的五种笨办法，全链路路线七步，压测标记逐跳透传表、InheritableThreadLocal 为什么不行，影子表 / 影子库 / 独立实例，按 P99 目标读单台容量，JDK 17 实测开环阶梯拐点和标记在线程池里丢失，容量计算器 |

## Redis

| # | 页面 | 内容 |
|---|------|------|
| 01 | [缓存穿透、击穿与雪崩](https://study.ainiya.de/redis/cache-problems.html) | 三种漏法怎么发生、布隆过滤器、互斥锁和逻辑过期、过期时间打散和高可用，十种防护的代价，数据库压力实验台 |
| 02 | [Redis 持久化 RDB 与 AOF](https://study.ainiya.de/redis/redis-persistence.html) | 拍照和记账、fork 与写时复制、三种刷盘策略、AOF 重写、混合持久化和多文件 AOF，宕机实验台 |
| 03 | [Redis 主从、哨兵与集群](https://study.ainiya.de/redis/redis-ha-cluster.html) | 全量和部分同步、哨兵怎么判死和换主、16384 个槽和 hash tag，故障转移演示和槽位计算器 |
| 04 | [Redis 数据结构与编码](https://study.ainiya.de/redis/redis-data-encoding.html) | 五种类型和八种编码、SDS 与 embstr、listpack 与 quicklist、渐进式 rehash、跳表，编码观察器 |
| 05 | [Redis 过期删除与内存淘汰](https://study.ainiya.de/redis/redis-eviction-expire.html) | 惰性删除加定期巡逻、八种淘汰策略、近似 LRU 的抽样和候选池、LFU 计数器，巡逻实验台和淘汰准确度对比 |
| 06 | [Redis 分布式锁](https://study.ainiya.de/redis/redis-distributed-lock.html) | 五次进化、令牌和 Lua 解锁、Redisson 看门狗，锁与事务的顺序、主从切换丢锁、RedLock 和 fencing token，事故实验台 |
| 07 | [Redis 线程模型与 IO 多路复用](https://study.ainiya.de/redis/redis-threading-io.html) | 单线程为什么快、select/poll/epoll、事件循环演示、慢命令怎么堵住所有人、I/O 线程和 Pipeline |
| 08 | [Redis 大 key 与热 key](https://study.ainiya.de/redis/redis-bigkey-hotkey.html) | 多大算大、危害和拆分，热 key 为什么加机器没用、本地缓存和复制打散，怎么发现，大 key 计算器和热 key 实验台 |
| 09 | [Redis Stream 与消息队列](https://study.ainiya.de/redis/redis-stream-mq.html) | List、Pub/Sub、Stream 三代对比，消费组、PEL、ACK 和认领，至少一次与幂等，延迟消息，消费组实验台 |
| 10 | [Redis Lua 脚本与事务](https://study.ainiya.de/redis/redis-lua-tx.html) | MULTI/EXEC/WATCH、出错为什么不回滚、Lua 的写法和 EVALSHA、Redis 7 Functions，最后一件库存两人抢 |
| 11 | [布隆过滤器与 HyperLogLog](https://study.ainiya.de/redis/redis-bloom-hll.html) | 位数组和 k 个哈希、误判率实验室、容量怎么算、抛硬币估人数、16384 个桶，UV 统计和选型 |
| 12 | [改完价，详情页还卖 399：先改库还是先删缓存、延迟双删、订阅 binlog](https://study.ainiya.de/redis/cache-consistency.html) | 先删后改为什么必卡、删不改、先改后删剩下的慢读竞态、延迟双删、订阅 binlog 删缓存、墓碑加版本号回填、交易靶场 6 种写法实测，竞态推演台 |
| 13 | [4 台机器各存一份 88 号：Caffeine 加 Redis 两级缓存](https://study.ainiya.de/redis/cache-multilevel.html) | 两级缓存读写路径、为什么广播删除再配短过期、先删 Redis 再广播、get(key, loader) 和桶锁、订阅断线丢消息与断线即清、CLIENT TRACKING / Redisson / JetCache 对比、refreshAfterWrite 版本差异，两级缓存推演台 |
| 14 | [88 号过期那一刻：缓存穿透、击穿、雪崩与大 key、热 key](https://study.ainiya.de/redis/cache-five-holes.html) | J07 第 3 个下钻知识点（第二圈）：交易靶场里实测穿透、击穿、雪崩三组对比，挡在前面、排队、打散、允许旧四类防法的取舍，重建锁对逻辑过期，大 key 堵住共享连接，HOTKEYS 找热 key，DEL 对 UNLINK，击穿实验台 |
| 15 | [锁过期时 A 还在查库：看门狗、fencing token 与 Lua 条件写](https://study.ainiya.de/redis/redis-lock-expire-fencing.html) | 锁是租约所以会过期、A 自己判断为什么不行、锁守卫与版本守卫（fencing token）、DEL 换墓碑、Redisson 看门狗挡不住进程停住、Lua 脚本 BUSY 与 NOSCRIPT、Redlock 之争，三条时间线 × 五种回填写法实验台 |
| 16 | [279 µs 里只有 2 µs 在 Redis：一条连接、一个线程上的排队](https://study.ainiya.de/redis/redis-event-loop-queueing.html) | J07 全景第 2、3 站下钻（第二圈）：一次 GET 拆成 8 段、主线程和共享连接两处排队、KEYS / BLPOP / 大 value 谁拖住谁、SLOWLOG 为什么看不见排队、IO 线程 7.2 到 8.x、Lettuce 超时与 FIFO 队列，谁会卡住实验台 |
| 17 | [648 字节的详情占 805 字节：Redis 8 的 kvobj、embstr 新门槛与存 String 还是 Hash](https://study.ainiya.de/redis/redis-encoding-memory.html) | J07 全景第 7 站第二圈：805 字节逐块拆解、Redis 7.2 和 8.2+ 一个 key 的两种拼法、embstr 门槛变成 key + 值 ≤ 41、String / Hash / JSON 四种存法实测、四个内存坑，字符串 key 内存计算器 |
| 18 | [第 617 个商品写不进去：Redis 写满以后的 OOM、淘汰与过期](https://study.ainiya.de/redis/redis-oom-eviction.html) | J07 第二圈：maxmemory 写满时哪些命令被拒（DENYOOM、Lua 脚本）、四种策略在交易靶场里赶走谁（连锁也赶）、过期 key 晚删造成的 OOM 窗口、淘汰时间预算与主动过期源码，全景链路实验台 |
| 19 | [88 号的锁有了两个主人：Redis 重启、切主以后丢了什么](https://study.ainiya.de/redis/redis-restart-failover.html) | J07 第二圈：一条 SET 回 OK 时在哪几处、重启时的 LOADING、切主丢掉的那一段、主库自动重启清空从库；Redis 8.10.3 实测四种持久化重启耗时、断网切主后锁有两个主人，附故障实验台 |

## Kafka

| # | 页面 | 内容 |
|---|------|------|
| 01 | [Kafka 消息可靠性与消费组](https://study.ainiya.de/kafka/kafka-reliability-group.html) | 六步学习法：acks 和 ISR、min.insync.replicas、offset 提交时机、消费组和 rebalance、幂等与死信，故障实验台和消费组实验台（关键行为本机集群实测） |
| 02 | [Kafka 存储：segment、索引、页缓存与零拷贝](https://study.ainiya.de/kafka/kafka-storage-zerocopy.html) | 分段和稀疏索引怎么查、页缓存为什么比 JVM 缓存好、sendfile 少了哪几次拷贝、retention 为什么不准、回放拖慢实时和 TLS 的代价，查找、零拷贝、页缓存三个实验台 |
| 03 | [积分加了两次，退款跑到了付款前面：幂等消费与顺序消息](https://study.ainiya.de/kafka/kafka-idempotent-ordering.html) | J08 第 8、2 站下钻：结果和位点不在一个事务、去重表与位点存业务库、顺序在哪几处被打乱、覆盖型用版本号累加型用去重、交易靶场 dup / order 实测，1000 单乱序与重复实验台 |
| 04 | [三台 broker 都倒了，谁能当 leader：Kafka 的 ISR、ELR 与 unclean 选举](https://study.ainiya.de/kafka/kafka-leader-election-elr.html) | 可靠性第二圈：机架断电后控制器的四张名单（Isr、Elr、LastKnownElr）、选举顺序、unclean 选举截掉已 ACK 消息和 offset 复用、kill -9 被移出 ELR、高水位冻结，Kafka 4.4.0 四个断电剧本实测，选主推演台 |
| 05 | [大促积压 100 万条：消费组的扩容上限、重平衡风暴与共享组](https://study.ainiya.de/kafka/kafka-backlog-drain.html) | LAG 曲线三种形状、加机器加分区为什么没用、活锁式重平衡风暴（经典协议 vs KIP-848）、车道 / 搬家 / 共享组 / 跳过过期四条路的实测速度，消化时间计算台 |
| 06 | [积分服务停了 8 天，消息已经被删：Kafka 的分层存储、日志压缩与位点过期](https://study.ainiya.de/kafka/kafka-tiered-compact.html) | 三样东西各自过期、分层存储的两截日志（上传、本地删除、远端读、远端过期）、日志压缩和墓碑、__consumer_offsets 与位点过期、按时间戳找回位置、远端挂了会怎样，一个段的晚年分步动画 |
| 07 | [交易靶场的五种消息：Kafka、RocketMQ、RabbitMQ、Redis Stream 怎么选](https://study.ainiya.de/kafka/mq-selection.html) | J08 怎么选第二圈：读完留不留、按组记位点还是按条记状态、日志派怎么补单条重试（重试 topic、共享组）、队列派怎么补回放（stream 队列）、确认那一刻消息在哪、四家这几年补的课，RabbitMQ 4.4.0 实测（读完就删、nack 不进死信、路由、原生延迟），五种消息选型台 |
| 08 | [退款比付款先到：状态机、跳号暂存与过期副作用](https://study.ainiya.de/kafka/kafka-reorder-statemachine.html) | 幂等与顺序第二圈：早到不是失败、每单连续序号三分类（旧的确认、下一号生效、跳号暂存）、状态机管合法序号管轮次、暂存和放行要同一把行锁、超时回查、过期短信不发，1000 单乱序重复并发丢失四种写法实测，9527 逐条推演台 |

## Java 并发

| # | 页面 | 内容 |
|---|------|------|
| 01 | [SynchronousQueue 与 LinkedTransferQueue](https://study.ainiya.de/juc/synchronous-transfer-queue.html) | 双重队列和双重栈、一次 CAS 完成交接、xfer 的四种模式、先自旋再 park、slack 与自链接、线程池里的后果、JDK 11 / 21 实测，分步演示和沙盘 |
| 02 | [ThreadPoolExecutor.execute 源码](https://study.ainiya.de/juc/threadpool-execute.html) | execute 的三个 if、ctl 的位、Worker 和 getTask、放进队列后的复查和线程退出前的检查、几件只能靠源码解释的怪事、各版本差异，线程调度实验台 |
| 03 | [AQS 源码](https://study.ainiya.de/juc/aqs.html) | state 加等待队列、独占和共享、Condition 的两条队、公平与非公平、JDK 8 和 17 / 21 两代源码对照、日常开发里哪些框架和 JDK 类用到了它，三个 JDK 实测和实验台 |
| 04 | [Java 内存模型](https://study.ainiya.de/juc/java-memory-model.html) | 写了不等于别人看到：重排序从哪来、happens-before 规则和推导、为什么只保证没有数据竞争的程序、volatile / synchronized / final 各保证什么、内存屏障和 VarHandle，可见性和重排序实测（JDK 17，ARM），双重检查锁分步推演 |
| 05 | [线程、线程状态与上下文切换](https://study.ainiya.de/juc/thread-state-context-switch.html) | Java 线程和内核线程 1:1、线程创建成本、六种状态和内核状态对照（RUNNABLE 也可能在 IO 里睡着）、读线程转储、两种上下文切换和怎么数、线程数公式、中断和守护线程，JDK 17 实测（/proc 对照、512 线程慢 36%、一次交接 3.9 微秒、新建线程 82 微秒），线程状态机实验台 |
| 06 | [JMM 下一圈：jcstress、CPU 缓存与伪共享](https://study.ainiya.de/juc/jmm-jcstress-cache.html) | Java 内存模型的下一圈：存储缓冲和失效队列、缓存一致性只管同一地址、x86 TSO 和 ARM 放宽了哪些重排序、volatile 和 CAS 在两种 CPU 上的指令、AQS 和 ConcurrentHashMap 里 volatile 读加 CAS 的模式、伪共享和 LongAdder；jcstress 0.16 在 ARM 上实测库存超卖（volatile 33.6%）、SB、MP（看到标志没看到数据 0.07%）和禁止结果 0 次，伪共享实测，先猜再看结果的实验台 |
| 07 | [synchronized 与锁升级、CAS 与原子类](https://study.ainiya.de/juc/synchronized-cas-atomic.html) | 对象头 mark word 的几种状态（JOL 实测无锁、thin lock、fat lock、偏向）、monitorenter / monitorexit 和异常表、轻量级锁和膨胀成 ObjectMonitor、wait / notify、偏向锁为什么被拿掉、CAS 在 ARM 和 x86 上的指令、ABA 实测、原子类和 LongAdder，五种写法吞吐实测（JDK 17，2 核 ARM），锁升级分步演示 |
| 08 | [AQS 下一圈：读写锁、StampedLock、Semaphore 与 JFR 找锁竞争](https://study.ainiya.de/juc/aqs-rwlock-jfr.html) | AQS 的下一圈：读写锁把 state 劈成两半、readerShouldBlock 和写锁饥饿、锁降级和升级死锁、StampedLock 乐观读和 validate、Semaphore 舱壁、JFR 的 jdk.JavaMonitorEnter / jdk.ThreadPark；JDK 17 实测四把锁读吞吐（读短时读写锁比普通锁慢、公平读写锁慢 75 倍、乐观读最快）、用 JFR 抓出锁里慢 SQL、Semaphore 限并发，先猜再看的实验台 |
| 09 | [ConcurrentHashMap 与阻塞队列](https://study.ainiya.de/juc/chm-blocking-queue.html) | HashMap 并发 put 丢数据实测（丢 4%～16%）、ConcurrentHashMap 的桶数组和三种特殊节点、putVal 的几条路（空桶 CAS、锁桶头、协助扩容）、TreeBin、分格计数、只保证单个方法原子（get 再 put 实测丢更新、merge 不丢）、Recursive update、初始容量，阻塞队列家族和 DelayQueue，JDK 17 反射实测，putVal 路径演示 |
| 10 | [线程池下一圈：怎么配、拒绝策略、动态调参与监控](https://study.ainiya.de/juc/threadpool-tuning.html) | 线程池的下一圈：用利特尔法则和 CPU 占比算线程数、按可接受排队时间定队列、四种拒绝策略把代价给了谁（实测 100 条通知三种策略丢 86 条、CallerRuns 让提交方慢 40 倍）、运行中先调最大再调核心（实测 2→16 积压 1 秒消完）、监控五个数、优雅关闭三步，参数计算器 |
| 11 | [ThreadLocal 与内存泄漏](https://study.ainiya.de/juc/threadlocal-leak.html) | 值存在线程的 ThreadLocalMap、key 弱 value 强的引用链、串号和三种泄漏、顺手清理与为什么不用引用队列、InheritableThreadLocal / TTL / ScopedValue，ThreadLocalMap 实验台 |
| 12 | [CompletableFuture 与异步编排](https://study.ainiya.de/juc/completablefuture-orchestration.html) | result 加 Completion 栈的结构、回调在哪个线程跑、thenCompose / thenCombine / allOf 与异常、默认池和超时不取消的坑、ThreadLocal 怎么带，回调线程先猜再看实验台 |
| 13 | [虚拟线程下一圈：什么时候用、pinning 的坑](https://study.ainiya.de/juc/virtual-threads-pinning.html) | 挂载卸载和载体线程、钉住的三种原因、trace 参数和 JFR 找钉住、ReentrantLock 修法与 JEP 491、什么时候不该用、和 J02 前八个知识点对照，载体线程甘特图实验台 |

## 网络

| # | 页面 | 内容 |
|---|------|------|
| 01 | [从输入 URL 到页面展示](https://study.ainiya.de/network/url-to-page.html) | 12 站全景、往返次数尺子、DNS 层级缓存、TCP + TLS 1.3 时序、慢启动、渲染阻塞、三次握手等设计取舍、Java 迷你浏览器实测（JDK 8 / 17 / 21）、往返计算器和 script 位置实验台 |
| 02 | [网络 IO 模型](https://study.ainiya.de/network/io-models.html) | 一万个连接要几个线程：五种 IO 模型的两段等待、连接便宜线程贵、Reactor 和 Tomcat NIO 连接器、事件循环为什么不能阻塞、HTTP 连接池和 keep-alive 等八个坑、BIO / NIO / 虚拟线程 1 万连接实测（JDK 17 / 21），keep-alive 连接分步演示 |
| 03 | [TCP：握手、挥手、TIME_WAIT 与粘包](https://study.ainiya.de/network/tcp-handshake-timewait-framing.html) | 连接是两端内核的两本账、三次握手为什么是三次、四次挥手和 CLOSE_WAIT、TIME_WAIT 为什么在先关的一方、字节流与长度前缀、Nagle × 延迟 ACK 的 40 ms、accept 队列，真实抓包逐段演示 |
| 04 | [Netty：EventLoop、Pipeline、ByteBuf](https://study.ainiya.de/network/netty-eventloop-pipeline-bytebuf.html) | EventLoop 终身绑定连接、Pipeline 入站出站方向、ByteBuf 双下标与引用计数、慢请求拖慢一个线程和漏 release 的实测、4.1→4.2 差异，EventLoop 阻塞实验台 |
| 05 | [RPC 原理：序列化、协议、服务发现、负载均衡](https://study.ainiya.de/network/rpc-serialization-discovery-lb.html) | 一次调用的八步、动态代理 Stub、自描述和约定结构的序列化、帧头与请求 id 多路复用、客户端发现与负载均衡、为什么这样设计，纯 JDK 迷你 RPC 实测（慢实例、坏实例、超时），负载均衡实验台 |
| 06 | [HTTP 客户端与连接池：超时怎么配](https://study.ainiya.de/network/http-client-pool-timeouts.html) | 一次调用的四段超时（拿连接、建连接、等响应、读响应）和总 deadline、读超时为什么不是总超时、池子满了在客户端排队、超时后对面照样做完、各客户端默认值对照，“哪个超时先到”实验台 |
| 07 | [HTTP 流式与 SSE：一个响应怎么一块一块地推](https://study.ainiya.de/network/http-streaming-sse.html) | 分块传输的原始字节、每一层缓冲为什么会让流式失效、SSE 的 event / data / id 格式、EventSource 只能 GET、SseEmitter 和 HttpClient 按行读、flush 与不 flush 的实测，缓冲模拟器 |

## 架构

| # | 页面 | 内容 |
|---|------|------|
| 01 | [三高知识地图](https://study.ainiya.de/arch/three-highs-map.html) | 高性能、高并发、高可用是同一本账：Little 定律算线程和连接、可用率串联相乘并联互补、超时舱壁降级为什么缺一不可、知识点挂在请求链路（含网络 IO、服务治理）和投产六关上、日常开发和投产两张清单、积分卡住时四种写法实测，线程账实验台 |
| 02 | [3 台 TC 挂了 2 台，下单直接报错：CAP、BASE 与一致性模型](https://study.ainiya.de/arch/cap-base-consistency.html) | 分区时拒绝还是先答、PACELC、一致性模型五级尺子、多数派与 W+R>N、BASE 软状态的期限和收尾、七个误用，3 副本抢券实验台 |
| 03 | [双击下单只出一张单：幂等设计——唯一键、状态机、去重表](https://study.ainiya.de/arch/idempotency-design.html) | 为什么必须由接收方去重、幂等的三个问题、唯一键的等锁与 1062、键同事务还是先提交、状态机的“从哪来归谁”、去重表与 Seata TCC fence、交易靶场 MySQL 实测，同一个键来两下实验台 |
| 04 | [一单写三个库：2PC/XA、TCC、Saga、本地消息表与 Seata](https://study.ainiya.de/arch/distributed-transactions.html) | 两阶段提交的不确定区、四种做法把中间态放在哪（XA 锁住 / TCC 冻结 / Saga 先做后补 / 本地消息表只管送到）、fence 挡住重发空回滚悬挂、Seata TM RM TC 与 AT TCC Saga XA 各管什么、MySQL 8.4 四段实测，四种做法 × 三种故障实验台 |
| 05 | [300 ms 超时，库存却冻了 2 件：时钟、超时与重试](https://study.ainiya.de/arch/clock-timeout-retry.html) | 超时 = 不知道的五种情况、查还是重做、退避抖动上限预算、墙上时钟 vs 单调时钟、Seata 判超时用谁的钟、比数不比钟，交易靶场实测和重试风暴实验台 |
| 06 | [tc-1 断网了，谁来接着拍板：Raft 选主与日志复制](https://study.ainiya.de/arch/raft-consensus.html) | 多数派重叠、任期与随机选举超时、RequestVote 与 AppendEntries、过半提交与 no-op、投票限制、PreVote 与 leader 租约、ReadIndex，tc-1 断网 13 步分步演示，MiniRaft 与 SOFAJRaft 1.3.14 实测换主 |
| 07 | [两个实例只许一个发：Redis、ZooKeeper、数据库三种分布式锁怎么选](https://study.ainiya.de/arch/distributed-lock-choice.html) | 锁记在哪、持锁者死了怎么放、换主丢不丢三个问题，ZooKeeper 临时顺序节点与会话、数据库行锁与租约行、SKIP LOCKED，kill -9 / 冻住 / 发得慢三种事故与 ZooKeeper 换 leader 实测，事故实验台 |
| 08 | [订单号 9527 从哪来：分布式 ID——号段与雪花算法](https://study.ainiya.de/arch/distributed-id.html) | id_alloc 一行加行锁、双 buffer 预取、雪花 64 位三种布局、机器号撞车、时钟回拨与重启回拨、Seata 改良雪花、ID 形状对 InnoDB 页分裂的实测，发号事故实验台 |
| 09 | [10 万个请求，只放进 2 万：限流算法](https://study.ainiya.de/arch/rate-limit-algorithms.html) | J12 第 3 个知识点：固定窗口交界处放进 2 倍、滑动窗口分桶、令牌桶的突发等于容量和懒计算、漏桶排队匀速，Gateway 按整秒补且 Redis 出错放行，单机 / Redis / 集群令牌三种放法，JDK 17 实测五种限流器和 Guava 先用后付，限流实验台 |
| 10 | [1000 张券、10 万人：秒杀与抢券](https://study.ainiya.de/arch/seckill-coupon.html) | J12 第 4 个知识点：直接扣 MySQL 卡在热点行，四种流派，削峰漏斗每层挡什么、挡错的代价，“决定”在 Redis、“记账”在 MySQL，切主回涨和重复消息靠条件更新和唯一键兜底，Redis 8.10 实测 GET 再 DECR 超发一倍、Lua 正好、售罄标记让 2 万请求只打 137 次 Redis，超发分步演示 |
| 11 | [机房断电以后：多活与容灾，RTO 和 RPO](https://study.ainiya.de/arch/multi-active-dr.html) | J12 第 6 个知识点：RTO 和 RPO 时间线，冷备、主备、同城双活、两地三中心、异地多活，光速决定同城同步、异地异步，等确认还是先回复，单元化和切不开的全局库存，脑裂和第三地仲裁，半同步悄悄退化，Redis 8.10 实测异步复制切主丢 11555 次已确认写入、WAIT 不丢但停写，各流派 RTO 时间线 |
| 12 | [预案写在纸上不算：故障演练与预案](https://study.ainiya.de/arch/chaos-drill-runbook.html) | J12 第 7 个知识点：预案五部分（触发、自动、人工、验证、回退），演练五步和爆炸半径、停止条件，ChaosBlade / Chaos Mesh / Toxiproxy，Redis 8.10 一主两从三哨兵实测杀主 RTO 42.1 秒（判定 30 秒）对 7.2 秒（5 秒）、RPO 0、旧主回来 10 秒的脑裂窗口，预案速查（先猜用户看到什么） |

## JDK

| # | 页面 | 内容 |
|---|------|------|
| 01 | [JDK 8、17、21、25](https://study.ainiya.de/jdk/jdk-8-17-21.html) | 四个 LTS 是怎么连起来的：5、6、7 留下的地基（内存模型、锁优化、invokedynamic、Fork/Join）、半年一班车和预览特性、四条主线（语言、并发、GC、平台治理）、50 个新特性各是什么、为什么加、怎么用（带示例）、record + sealed + 模式匹配、强封装、ScopedValue 的设计取舍、8 / 21 / 25 写法对照与升级五步、十二个升级坑、25 之后的 27 和 29，升级检查器 |

## JVM

| # | 页面 | 内容 |
|---|------|------|
| 01 | [JVM 内存结构](https://study.ainiya.de/jvm/jvm-memory-structure.html) | 一个 Java 进程的内存分成哪几块：线程私有的栈、共享的堆、堆外的元空间和直接内存，栈和堆怎么配合、对象头和对象大小、为什么分代，六种 OOM 怎么认、容器被杀的原因，实测撑爆四块内存（JDK 17），分代实验台 |
| 02 | [G1 和 ZGC 怎么回收](https://study.ainiya.de/jvm/g1-zgc.html) | 回收的三件事谁要停下来做、G1 的 Region 和记忆集、并发标记与混合回收、停顿预测、ZGC 的染色指针、读屏障和并发搬迁、为什么一个停顿里搬一个边跑边搬、六个坑和版本差异，实测 Parallel、G1、ZGC 四组对比（JDK 17），G1 和 ZGC 实验台 |
| 03 | [new 一个对象的全过程：分配、对象头与内存布局](https://study.ainiya.de/jvm/jvm-object-new-layout.html) | new 的五步、TLAB 快速 / 慢速路径、mark word 与类指针、字段重排与对齐、压缩指针为什么卡在 32 GB、JOL 与关 TLAB 实测，对象布局实验台 |
| 04 | [GC 日志与调优：先定目标，再动参数](https://study.ainiya.de/jvm/jvm-gc-log-tuning.html) | 三个目标的取舍、一行日志怎么读、占比 / 最长停顿 / 回收后占用三样数、Parallel 固定分代 vs G1 自适应、交易靶场大促与泄漏实测、GC 日志体检台 |
| 05 | [类加载与双亲委派：SPI 为什么要打破它](https://study.ainiya.de/jvm/jvm-classloading.html) | 类的一生、三层加载器与 loadClass 源码、类的身份、为什么先问上级、SPI 借 TCCL 反向加载与 Tomcat 子优先、元空间泄漏实测，委派走一遍实验台 |
| 06 | [JIT、逃逸分析与常见的性能误区](https://study.ainiya.de/jvm/jvm-jit-escape.html) | 分层编译、内联和去虚化、逃逸分析与标量替换、去优化、热点 NPE 丢堆栈和预热等坑、六个性能误区，逃逸判定台 |
| 07 | [JVM 故障排查：OOM、频繁 Full GC、CPU 飙高](https://study.ainiya.de/jvm/jvm-troubleshooting.html) | 常见误判、先留现场再分两条路线、OOM 抛给了谁、Full GC 后降不降、shallow 和 retained、nid 对到一行、交易靶场三个雷实测（MAT、Humongous、JFR 分配和方法采样）、启动参数模板，排查练习台 |
| 08 | [容器里的 JVM：内存和 CPU 限制](https://study.ainiya.de/jvm/jvm-container.html) | cgroup 限额写在哪、JVM 读到后怎么定堆和 GC 和线程数、内核怎么杀进程和节流、堆按比例切加堆外逐块封顶、版本差异，容器内存预算台 |
| 09 | [容器里的 JVM 怎么起得快：CDS、AOT 缓存和别的路](https://study.ainiya.de/jvm/jvm-startup-aot-cache.html) | 容器里的 JVM 第二圈（J14 第 4 个知识点）：启动慢慢在类的加载、解析、校验、链接，AppCDS 和 JDK 24 / 25 的 AOT 缓存（JEP 483 / 514 / 515）训练一次存成文件，对不上就退回普通启动，CRaC 和 Native Image 对照；本机 1 核容器实测 JDK 21 6.2 s → 4.5 s、JDK 25 6.4 s → 3.8 s、7706 个类里 7438 个来自缓存、touch 一个 jar 缓存全失效、懒加载只快 5%，启动时间换算发布和回滚的实验台 |

## Java 基础

| # | 页面 | 内容 |
|---|------|------|
| 01 | [面向对象、接口与抽象类、泛型和类型擦除](https://study.ainiya.de/javase/oop-generics-erasure.html) | J01 第 1 个知识点：封装靠访问控制和防御性复制、多态靠运行时查方法表、接口与抽象类的分工和菱形问题、sealed 与 record、泛型从源码到运行的五步（编译期检查、擦除插 checkcast、Signature 留底、对象不知道元素类型）、为什么非擦除不可、桥方法与 TypeReference，JDK 17 实测与分步演示 |
| 02 | [常用集合怎么选：ArrayList、LinkedList、Set、Queue](https://study.ainiya.de/javase/collections-choose.html) | J01 第 2 个知识点：按“怎么找”选 List / Set / Map / Queue，ArrayList 扩容与头插、LinkedList 节点与缓存不友好、哈希与红黑树、ArrayDeque 环形数组、PriorityQueue 二叉堆与 DelayQueue，交易靶场订单簿，8 个场景先猜再看 JDK 17 实测 |
| 03 | [HashMap：哈希、扩容、树化](https://study.ainiya.de/javase/hashmap-internals.html) | J01 第 3 个知识点（过关题）：hashCode、扰动与 (n−1)&hash 定位，put 全过程 9 步，负载因子与翻倍扩容的高低位拆分，树化 8 / 6 / 64 与泊松分布，2 的幂对比 Hashtable 素数取模，并发写丢数据与 JDK 7 成环，put 模拟器与 JDK 17 反射实测 |
| 04 | [HashMap 的亲戚们：LinkedHashMap、WeakHashMap、ThreadLocalMap](https://study.ainiya.de/javase/hashmap-relatives.html) | HashMap 的下一圈：LinkedHashMap 的双向链表与三个钩子、访问顺序加 removeEldestEntry 做 LRU，WeakHashMap 的弱引用与 ReferenceQueue，ThreadLocalMap 挂在线程上、开放寻址与 0x61c88647，key 弱 value 强与线程池里的串号和内存泄漏，LRU 模拟器与 JDK 17 实测 |
| 05 | [Lambda、Stream、record、模式匹配：编译后变成了什么](https://study.ainiya.de/javase/lambda-stream-record.html) | J01 新特性的下一圈（机制）：invokedynamic 和四个引导方法，Lambda 的隐藏类与捕获，Stream 惰性流水线、Sink 链、短路与有状态操作，parallelStream 的公共池，record 的规范构造器与 ObjectMethods，sealed + switch 的 typeSwitch 与穷举检查，Stream 流水线分步演示，JDK 17 / 21 实测 |
| 06 | [异常、反射、注解与动态代理：Spring 下面那一层](https://study.ainiya.de/javase/exception-reflection-proxy.html) | J01 第 5 个知识点的下一圈（JDK 层）：受检与非受检、异常贵在填栈与 OmitStackTraceInFastThrow、try-with-resources 与 suppressed，Method.invoke 的 inflation 与 JDK 18 的 MethodHandle 实现、强封装，注解的保留策略与“注解对象也是代理”，生成的 $Proxy 类和异常表，手写事务 + 审计拦截器，代理调用分步演示，JDK 17 实测 |
| 07 | [IO 与 NIO 基础：字节怎么进来，怎么出去](https://study.ainiya.de/javase/io-nio-basics.html) | J01 第 6 个知识点的下一圈（API 与字节）：流的装饰器、字符集与乱码、缓冲为什么快（strace 数系统调用：一次一字节 200 万次对 263 次）、ByteBuffer 三指针与 flip / compact、堆内与直接缓冲、FileChannel.transferTo 与 sendfile、Files 工具，交易靶场导出导入，ByteBuffer 演示，JDK 17 实测 |
| 08 | [数据结构与算法：日常和面试够用的那部分](https://study.ainiya.de/javase/algorithms-everyday.html) | J01 最后一个知识点：先按数据量估复杂度，按最频繁的操作选结构，二分的不变式、Top K 小顶堆、滑动窗口限流、TimSort 与双轴快排及比较器约定，红黑树插入分步手推（和 TreeMap 反射实测逐步一致），面试题型地图，交易靶场四道题，JDK 17 实测 |

## RocketMQ

| # | 页面 | 内容 |
|---|------|------|
| 01 | [改库和发消息怎么一起成功：RocketMQ 的事务消息、定时消息、顺序消息](https://study.ainiya.de/rocketmq/rocketmq-tx-delay-order.html) | 半消息 + 回查、延迟级别与时间轮、选队列与锁队列，交易靶场实测（进程死在四个位置、定时取消、三种顺序消费），回查时间线实验台 |

## 微服务

| # | 页面 | 内容 |
|---|------|------|
| 01 | [下单为什么要穿过五个服务：服务怎么拆](https://study.ainiya.de/cloud/service-split.html) | 单体四个痛点、模块化单体能解决哪些、按层按表按领域三种切法、拆开后原来免费的六样东西、变更事务运行时三种耦合、拆多细五条、交易靶场五个服务的理由、六个误用、绞杀者迁移与 co-change 找边界，三种切法推演台 |
| 02 | [inventory-2 下线了，订单服务多久知道：Nacos 注册发现与配置中心](https://study.ainiya.de/cloud/nacos-registry-config.html) | 写死地址、DNS、Nginx 各疼在哪，Eureka、ZooKeeper、Consul、Nacos、K8s 对比，注册订阅推送与 500 ms 合并、连接即心跳与 20 秒探测、配置推送与重新绑定、1.x 心跳为什么被换掉、Nacos 3.3.0 七种情况实测掐表、六个坑与版本差异，调用方误发掐表台 |
| 03 | [inventoryClient.reserve() 背后：OpenFeign、Dubbo 与负载均衡](https://study.ainiya.de/cloud/feign-dubbo-loadbalancer.html) | 手写 RestClient 疼在哪、OpenFeign / HTTP Service Clients / Dubbo / gRPC 对比、启动时接口变代理、调用栈一路到真实 IP、两层缓存、轮询只数次数、客户端负载均衡为什么赢、Dubbo 默认值对照、下线后又被调 32 秒实测，四种挑法实验台 |
| 04 | [1024 的请求进门之前：Spring Cloud Gateway、路由与鉴权](https://study.ainiya.de/cloud/gateway-route-auth.html) | 各自对外和只放 Nginx 疼在哪、Nginx / APISIX / SCG / Server MVC / Ingress 对比、找路由排过滤器挑实例转发、4 个事件循环线程、先删再写身份头、为什么选事件循环、阻塞过滤器 201→19 个/秒与默认无响应超时实测、六个坑与 4.3 改名，事件循环实验台 |
| 05 | [inventory-2 慢了，下单怎么还能降级：限流、熔断、降级与 Sentinel](https://study.ainiya.de/cloud/sentinel-circuit-breaker.html) | 雪崩怎么传上去、只有超时吞吐掉到 6% 实测、Hystrix / Sentinel / Resilience4j / 网格对比、熔断器状态机源码细节、按资源挡不按实例、限流和降级各算什么、半开放 1 个和放 10 个、交易靶场熔断开关三轮实测、六个误用，熔断调参台 |
| 06 | [1024 先用上新版：灰度发布与流量治理](https://study.ainiya.de/cloud/gray-release.html) | 全量发布和只换一台疼在哪、滚动 / 蓝绿 / 金丝雀 / 功能开关 / 泳道对比、入口打一次标、hint 挑实例与找不到就退回全部、过滤层和缓存层的顺序、标记透传、先下线等缓存再停、五实例实测（写反顺序灰度失效、kill 失败 295 次对 0 次），发版计算器 |
| 07 | [五个部件来自两个家族：Spring Cloud 与 Spring Cloud Alibaba 怎么选](https://study.ainiya.de/cloud/spring-cloud-vs-alibaba.html) | 全景每个部件来自哪个家族、Netflix 组件退场、纯 Spring Cloud / 混用 SCA / K8s 原生三种组合、Commons 定接口 SCA 填实现、Boot 牵头的版本对应表、为什么是版本列车、五种组合实测（只升一条线就找不到类、Boot 4.1 配 2025.1 能用）、五个坑与老组件迁移，版本对照器 |

## 搜索

| # | 页面 | 内容 |
|---|------|------|
| 01 | [商家 301 搜“键盘”：Elasticsearch 的倒排索引、分片、写入和查询](https://study.ainiya.de/search/es-inverted-index-shards.html) | J11 知识点 4：商家查询订单库为什么不擅长、LIKE / FULLTEXT / 异构索引表、ES vs OpenSearch vs OLAP、倒排索引与分词器（standard 把“键盘”拆成两个字，实测多命中 1.6 万单）、text vs keyword（动态映射 term 查不到）、分片路由、缓冲 + translog + 每秒 refresh 的近实时（实测 0.5～0.9 s 可见）、query then fetch 与 1 万条上限，倒排索引演示台 |
| 02 | [下单 1 秒后商家才搜得到：MySQL 到 ES 的同步（binlog、Canal、一致性）](https://study.ainiya.de/search/mysql-to-es-sync-canal.html) | J11 知识点 5：代码里写 ES / 扫表为什么不行、Canal / Debezium / Flink CDC、ROW 事件与前后镜像、Canal 装成从库（1.1.8 才认 MySQL 8.4 的 SHOW BINARY LOG STATUS）、写成功才 ack 的至少一次与幂等、按订单号分区和外部版本号（实测乱序 148 → 0）、提交到可搜约 0.8 s 的拆解、binlog 被清理后 1236 停摆与全量重灌，乱序演示台 |

## 可观测与排查

| # | 页面 | 内容 |
|---|------|------|
| 01 | [一个请求，三样数据：日志、指标、链路三件套](https://study.ainiya.de/observability/logs-metrics-traces.html) | 三种数据形状（聚合的数、一次事件、一棵 span 树）和成本特征，ThreadLocal 与 traceparent 传上下文，trace_id 进 MDC 和 exemplar，Observation 一次埋点出指标和 span，换线程丢 traceId、高基数标签、默认采样 10%、_created 后缀被吞，Spring Boot 3.5 实测，一个请求的分步动画 |
| 02 | [从一个数到一通电话：Prometheus 加 Grafana，指标和告警怎么设](https://study.ainiya.de/observability/prometheus-alerting.html) | 拉模式抓取、时间序列、rate 和 histogram_quantile、告警 pending 到 firing、Alertmanager 分组抑制路由，本机重演凌晨三点（3 实例 + Prometheus 3.16 + Alertmanager 0.35）测出错误率告警 117 秒、等连接告警 72 秒，空结果、实例挂了不响、平均值摊平等坑，燃烧率告警，告警延迟计算器 |
| 03 | [慢在哪一段：链路追踪，OpenTelemetry 和 SkyWalking](https://study.ainiya.de/observability/tracing-otel-skywalking.html) | agent 类加载时织入计时、Context 和 traceparent 传上下文、线程池自动续上、BatchSpanProcessor 和 OTLP、Collector 尾部采样，两个服务挂 OTel agent 2.33 进 Jaeger 2.23 实测复现 3 秒空白的 trace，MQ 断链、网关丢头、两套链路打架，和 SkyWalking 对比，瀑布图自身耗时阅读器 |
| 04 | [进 JVM 看一眼：Arthas 线上诊断](https://study.ainiya.de/observability/arthas-diagnosis.html) | Attach API 加载 agent、只读命令和 retransformClasses 增强命令、只看得到增强后进入的调用，本机复现全景第 9 站：thread 找到 10 个对账线程、栈里事务等渠道、vmtool 读出池子 10 active 4 waiting、jad、trace 20 秒 100% 在 queryOrder、watch 参数返回值，高频 trace、忘了 stop、容器 attach、热改代码等坑，增强时机时间线 |
| 05 | [先止血，再找因：排查方法论，从现象到根因](https://study.ainiya.de/observability/triage-method.html) | 第二圈：值班排查七步路线（定级、止血先留现场、RED 先整体、按实例和 USE 拆、链路往下剥、问变更、假设验证），RED、USE、变更优先、科学方法、事故指挥各管一段，先重启、确认偏误、修症状、没发布就没变更等误用，证据引用前几页实测，凌晨三点排查推演 |
| 06 | [对事不对人：故障复盘，时间线、根因、改进项](https://study.ainiya.de/observability/postmortem-review.html) | 复盘七步、对事不对人、瑞士奶酪模型、五个为什么分清根因诱因和促成因素、MTTD 和 MTTR 各由哪类改进缩短，用 Prometheus 实测原始事件自动生成时间线，全景那次故障的完整复盘文档，改进项评审器，四个刻意练习 |

## 云原生与交付

| # | 页面 | 内容 |
|---|------|------|
| 01 | [改一行代码，只推一层：Docker 镜像分层与多阶段构建](https://study.ainiya.de/cloudnative/docker-image-layers.html) | J14 第 1 个知识点：镜像是按内容寻址的一叠只读层、manifest 和摘要、overlay2 可写层与 copy-up、whiteout，BuildKit 缓存键和“一层失效上面全失效”，多阶段构建，Spring Boot 四层 jar；本机实测单阶段 650 MB 对多阶段 336 MB，改一行代码推 68.2 MB / 21.3 MB / 3.9 KB，删文件不变小、构建参数留在历史里、shell 形式 ENTRYPOINT 停机 10 秒，改哪层推多少实验台 |
| 02 | [只说想要什么：Kubernetes 核心对象与控制循环](https://study.ainiya.de/cloudnative/k8s-core-objects.html) | J14 第 2 个知识点：声明式 API 和水平触发的控制循环、控制器只和 API Server 说话、标签选择器代替点名，Pod、ReplicaSet、Deployment、Service、EndpointSlice、Ingress 和 Gateway API（ingress-nginx 已归档）；本机 kind 1.37 实测删 Pod 0.3 秒建替补、改标签被放弃、滚动 26 秒、回滚 24 秒和 kubectl 回滚提醒，maxSurge / maxUnavailable 滚动实验台 |
| 03 | [装得下、活着、能干活：requests、limits、探针和 HPA](https://study.ainiya.de/cloudnative/k8s-resources-probes.html) | J14 第 3 个知识点：requests 是预订、limits 是上限，CPU 可压缩被限速、内存不可压缩被杀，QoS 三个等级，Pod 被 OOMKilled 和 Java 抛 OOM 的区别（地图过关标准），startup / readiness / liveness 三种探针，HPA 公式、容差和稳定窗口；本机 kind 实测 -Xmx=limit 被杀 137 日志无 OOM、75% 抛 Java OOM 进程还活着、只配 liveness 100 秒重启 5 次、startupProbe 48 秒 Ready、HPA 1→5→1，容器内存账本实验台 |
| 04 | [换版本不断流、出事能秒回：CI/CD 与滚动、蓝绿、金丝雀](https://study.ainiya.de/cloudnative/cicd-release-strategy.html) | J14 第 5 个知识点：构建一次的不可变镜像、拉式 GitOps 部署（Argo CD selfHeal、git revert 回滚），重建 / 滚动 / 蓝绿 / 金丝雀 / 特性开关的取舍，新旧并存要前后兼容；本机 kind 实测滚动没有 preStop 失败 5 次、加 preStop 0 次、滚动回滚 27 秒，蓝绿 8 个 Pod、切换和回切 1 秒内 0 失败，按副本数金丝雀 19.7%，同一个 bug 三种策略各让多少订单失败的实验台 |
| 05 | [137、143 和那份没加密的密码：Linux 信号、启动脚本、配置和密钥](https://study.ainiya.de/cloudnative/linux-config-secrets.html) | J14 第 6 个知识点（动手技能）：PID 命名空间里 1 号进程只收装了处理函数的信号、exec 和 trap、退出码 128+N，ConfigMap 走环境变量 / 目录挂载 / subPath 的三种更新方式，Secret 在 Git、API、etcd、文件、环境变量里的样子，kubectl debug 临时容器；本机 kind 实测没写 exec 删 Pod 30.6 秒、写了 0.6 秒，目录挂载 60～67 秒才变、env 和 subPath 不变，etcd 里搜到明文密码，五个刻意练习和退出码解码器 |
| 06 | [给 agent 的命令造个笼子：Linux 进程、权限与容器隔离](https://study.ainiya.de/cloudnative/linux-process-isolation.html) | AI 站 04 的补给：子进程默认继承一切、用户和能力、rlimit 和 cgroup、七种 namespace、容器参数逐个讲，四层笼子实测拦住什么，分步动画 |

## 架构设计与团队

| # | 页面 | 内容 |
|---|------|------|
| 01 | [一句话里藏着 4 块钱：需求分析与业务建模](https://study.ainiya.de/design/requirements-modeling.html) | 业务方的一句话是压缩过的解法：丢了目标、默认规则和没想过的情况；目标追问、算例映射、逆向清单、事件序列和名词表，把“满 300 减 40 要能和券叠加”还原成 6 条规则和 7 个能跑的算例（本机实测“加个 if”只过 3 个），六个坑和团队规范，“同一句话几种读法”实验台 |
| 02 | [同一个词，两边是两个东西：DDD 限界上下文、聚合、领域事件](https://study.ainiya.de/design/ddd-bounded-context-aggregate.html) | 限界上下文是语言的边界（“优惠”在营销是规则、在订单是事实），聚合是一致性的边界（只圈住必须同一事务成立的不变量），边界之外只存 id、靠领域事件最终一致；防腐层、上下文映射、核心域；交易靶场的订单和营销两个上下文本机走一遍（改规则后按快照退 104.49，重算是 101.59），七个坑，预算放进下单事务还是发事件的实验台 |
| 03 | [先把边界守住，再决定拆不拆：单体、模块化、微服务的演进](https://study.ainiya.de/design/arch-evolution-modular-monolith.html) | 逻辑边界、代码边界、部署边界是三样东西：前两样便宜先要，部署边界贵且难退，等证据；大泥球、模块化单体、分组部署、独立服务四级台阶各得到什么付出什么，什么算该走下一步的证据；本机用 Spring Modulith verify() 抓出越界引用和成环；分布式单体等六个坑，绞杀者、模块事件；“现在该站第几级”实验台 |
| 04 | [选了什么、放弃了什么、为什么：技术选型与 ADR](https://study.ainiya.de/design/tech-selection-adr.html) | 选型是在写下来的约束里挑活得下来又最便宜的方案：约束先写、候选至少三个含维持现状、硬约束淘汰、活下来的比代价；哪些决定值得记，一页 ADR 每一节回答什么，只追加不修改；交易靶场三条 ADR 全文，本机把格式约定写成检查（3 条通过、2 条反例各 4 个问题）；六个坑，评分表、原型、退出成本；“换一条约束赢家换不换”实验台 |
| 05 | [420 行 if/else 怎么拆：设计模式，到 Spring 和 MyBatis 里去认](https://study.ainiya.de/design/design-patterns-in-frameworks.html) | 设计模式是同一个手法：把会变的做成对象，让不变的骨架去调它；从“什么在变”认策略、模板方法、责任链、代理（装饰、工厂、观察者、适配器一表带过），每个对照 Spring 6.2 和 MyBatis 3.5 源码里的类；交易靶场的算价先搬后改（30 组比对一致，加满减只多一个类，顺序换了差 4 元）；六个误用，lambda 写法；链的顺序实验台 |
| 06 | [写给挑错的人看：技术方案文档与评审](https://study.ainiya.de/design/design-doc-review.html) | 方案文档的任务是让别人在写代码之前用最少的时间找到最贵的错：八节各回答什么（算例、目标和非目标、放弃的方案、风险和谁定的、灰度回滚和老数据、待定问题），每拨读者看哪几节；评审先各自读写批注、会上只谈没谈拢的、散会前有结论和负责人；交易靶场方案的草稿和定稿全文，本机检查（v1 报 9 条，v2 通过）；七个坑，事前验尸、评审清单；“你来当评审人”找漏洞实验台 |
| 07 | [先让改动变容易，再做那个容易的改动：重构与偿还技术债](https://study.ainiya.de/design/refactoring-tech-debt.html) | 重构是不改变看得见的行为、只改内部结构，安全来自有东西证明行为没变：特征测试钉住老行为（连老毛病一起）、两顶帽子、小步搬、线上双跑比对、功能开关；技术债看利息不看丑不丑；本机实测：搬的时候顺手修一个舍入，108 组测试红 10 组、一万笔双跑差 1298 笔，原样搬差异为 0；七个坑，接缝、先扩展后收缩；“这笔债多久回本”实验台 |
| 08 | [它写得很快，你得知道哪里不能信：AI 辅助研发](https://study.ainiya.de/design/ai-assisted-dev.html) | AI 助手不知道没写下来的事、给的是最合理的而不是验证过的、不为结果负责：哪些活适合交给它，任务说明的五样（目标、上下文、约束、验收、输出），验收要用不是它出的题；本机实测：四份手写的有错实现自测都是 12/12，分别被签字的算例、特征测试、退款入口的算例拦住，全文搜索核出第 7 个入口；七个坑和团队约定，项目说明文件；“哪道关拦哪种错”实验台 |
| 09 | [让一个组都这样做：技术领导的规范、Code Review、带人](https://study.ainiya.de/design/tech-lead-review-mentoring.html) | 带一个组，产出是整个组的代码；规范、Code Review、带人做的是同一件事：把一个人脑子里的判断变成不依赖他在场的东西；规范的三层（机器强制、模板清单、文字约定），评审先看设计、小 PR 和一个工作日内回复互相咬着，委派阶梯和具体的反馈；本机把五条合并请求约定写成检查（三个样例 1 个通过、2 个共报 7 个问题）；八个坑，规范的演进、对事不对人的复盘；评审速度和 PR 大小实验台 |

## 算法基础

| # | 页面 | 内容 |
|---|------|------|
| 01 | [全景：撮合引擎的一天——算法基础 25 课学什么](https://study.ainiya.de/algo/pano-algo-trading-day.html) | 算法基础系列的课程全景：一张订单从网关到回测的 12 站，每站对应的数据结构和算法、六圈 25 课的顺序和状态、预测题，12 站分步演示 |
| 02 | [算法要用的数学：幂、对数、取整、取模、求和、排列组合](https://study.ainiya.de/algo/math-basics.html) | 算法基础第 0 课（前置）：幂与对数是一对、四种取整、% 的符号从哪来、求和式就是循环次数、排列组合乘法原理、看数据范围定复杂度、为什么模 1e9+7，Java Math 的六个坑，复杂度耗时实验台 |
| 03 | [从电灯开关到“你好”：计算机怎样表示数据](https://study.ainiya.de/algo/data-representation.html) | 算法基础第 1 课：十进制机器为什么输给二进制、晶体管到字节的五层、补码钟面、IEEE 754 里的 0.1、码点和 UTF-8、数组下标与 log n 从哪来，比特解读器实验台 |
| 04 | [数组为什么快：连续内存、缓存行和 O(1) 下标](https://study.ainiya.de/algo/array-why-fast.html) | 算法基础第 2 课：链表为什么输、地址怎么算、存储层级、缓存行与预取、Java 三种数组的布局（JOL）、按列慢 14 倍的实测，缓存模拟器实验台 |
| 05 | [大 O 是怎么数出来的：操作次数、最坏和平均、摊还与 log n](https://study.ainiya.de/algo/big-o-counting.html) | 算法基础第 3 课：数最内层操作的次数、扔掉常数和小项、log n 来自按比例砍半（二分分步动画、递归树）、最好 / 平均 / 最坏与 HashMap 树化、摊还与 ArrayList 1.5 倍扩容、大 O 为什么扔常数，JDK 17 实测计数与双倍法，扩容策略实验台 |
| 06 | [链表与空间换时间：多存几根指针，撤单就是 O(1)](https://study.ainiya.de/algo/linked-list.html) | 算法基础第 4 课：节点散放靠 next 串起来、插删就是改指针（撤单 + 追加分步动画）、O(1) 的前提是拿着节点、哨兵消掉头尾特例、空间复杂度和递归栈溢出、空间换时间逐块数字节（JOL 98.5 对 28 字节）、单向和双向的取舍，常用集合时间空间速查与空间换时间清单，JDK 17 实测撤单和遍历 |
| 07 | [栈、队列和环形数组：一块数组首尾相接，两头都是 O(1)](https://study.ainiya.de/algo/stack-queue-ring.html) | 算法基础第 5 课：栈和队列是进出规则、数组栈天生 O(1)、队列下标绕回成环、空满分不清的三种解法、& 掩码与负数、扩容先拆直、撮合入口为什么用定长环，ArrayList / LinkedList / ArrayDeque / 环形数组实测对比，朴素与环形并排的分步动画 |
| 08 | [堆和优先队列：订单簿按价格排队，最优价 O(1) 看、O(log n) 进出](https://study.ainiya.de/algo/heap-priority-queue.html) | 算法基础第 6 课：朴素做法实测对比、完全二叉树放进数组、上浮和下沉、为什么只排父子、PriorityQueue 撮合簿、五个坑、算法常用函数速查（7 组本机实测）、按价位聚合的真实订单簿，堆的分步动画 |
| 09 | [单调栈和单调队列：过去 60 秒最高价，每笔 O(1)](https://study.ainiya.de/algo/monotonic-stack-queue.html) | 算法基础第 7 课：被压住的永远翻不了身、单调队列不变式和三步操作、单调栈找下一个更高价、摊还 O(1)、四种做法实测对比、六个坑、单调栈题型表，窗口 3 秒的分步动画 |
| 10 | [哈希表：从 hashCode 到冲突和扩容](https://study.ainiya.de/algo/hash-table.html) | 算法基础第 8 课（HashMap 页的下一圈）：哈希函数打散、生日悖论、负载因子与探测次数实测对 Knuth 公式、线性探测和墓碑删除、扩容摊还、开放寻址 vs 拉链、long 原语集合对比 HashSet<Long> 内存实测、六个坑，8 格线性探测分步动画 |
| 11 | [二分查找：边界怎么写才不出错](https://study.ainiya.de/algo/binary-search.html) | 算法基础第 9 课：找由假变真的分界线、左闭右开不变式、lowerBound / upperBound 拼出所有查法、为什么不用闭区间、3000 万笔从头扫 vs 二分实测、七个坑（溢出、死循环、重复元素、负返回值、降序、LinkedList、端点）、二分答案，16 笔成交的分步动画 |
| 12 | [排序：快排、归并、TimSort 和稳定性](https://study.ainiya.de/algo/sorting.html) | 算法基础第 10 课：两种分而治之、Lomuto 划分、n log n 下界、稳定性和对账误报、TimSort 的 run 和跳跃合并、JDK 为什么基本类型用快排对象用 TimSort、500 万成交号四种排序实测、六个坑和外部排序，Lomuto 划分分步动画 |
| 13 | [双指针与滑动窗口：每个指针只往前走](https://study.ainiya.de/algo/two-pointers.html) | 算法基础第 11 课：为什么不用回头（非负的单调性）、同向窗口进和缩、时间窗口成交量、快慢去重和对撞凑单的不变式、双指针 vs 前缀和、10 万笔实测对拍、五个坑（负数、if 缩窗、溢出、按笔数、无序）、窗口题型表，最短放量段分步动画 |
| 14 | [前缀和与差分：任意时间段成交量 O(1)](https://study.ainiya.de/algo/prefix-sum.html) | 算法基础第 12 课：两个前缀相减、P 多一格的约定、差分只改两个端点、前缀和 + 哈希数合计为 K 的段、为什么能处理负数而最大值不行、100 万次查询实测、六个坑、二维前缀和与树状数组，差分算每秒挂单数的分步动画 |
| 15 | [递归与二叉树遍历：盘口从优到劣，就是一次中序遍历](https://study.ainiya.de/algo/recursion-tree.html) | 算法基础第 13 课：为什么树要一个栈、递归的三句话、前中后序只差一行、调用栈怎么记岔路、递归深度 = 树高、递归 vs 显式栈、退化树栈溢出实测、五个坑、前序 + 中序还原树和 Morris，中序遍历的树 + 调用栈分步动画 |
| 16 | [二叉搜索树与红黑树：撤单多、要盘口，为什么换 TreeMap](https://study.ainiya.de/algo/red-black-tree.html) | 算法基础第 14 课：堆为什么撤单慢、旋转不改中序、红黑树就是 2-3-4 树、树高上界、红黑树 vs AVL、TreeMap 盘口（价位 + 同价队列 + 按号撤单）、真实 TreeMap 树高和撤单实测、五个坑，一路上涨的价位插进红黑树的分步动画 |
| 17 | [B+ 树与跳表：两种多层索引，一个省磁盘，一个省旋转](https://study.ainiya.de/algo/bplus-skiplist.html) | 算法基础第 15 课：扇出决定树高、数据只放叶子和叶子链表、跳表的随机层数和 span 排名、p 取 1/4 的理由、B+ 树 vs 跳表 vs 红黑树、扇出与读页数和跳表层数实测、五个坑（函数条件、深分页、同分、弱一致、小 ZSet），跳表查找和排名分步动画 |
| 18 | [图的表示、BFS 与 DFS：从 1024 出发，找出所有关联账户](https://study.ainiya.de/algo/graph-bfs-dfs.html) | 算法基础第 16 课：图 = 树 + 环，visited 何时标记、BFS 为什么给出最少跳数、DFS 换栈、邻接矩阵 / 邻接表 / CSR、BFS vs DFS、20 万账户内存和耗时实测、五个坑（绕圈、标记太晚、递归太深、超级节点、方向），账户关联图 BFS 分步动画 |
| 19 | [并查集：账户一对对合并成团伙，查“是不是一伙”几乎 O(1)](https://study.ainiya.de/algo/union-find.html) | 算法基础第 17 课：一伙一棵树、代表是根、按大小合并为什么树高 ≤ log n、路径压缩、为什么只答“是不是一伙”、四个版本最坏输入和 100 万条边流式实测、五个坑（不找根、链、递归 find、拆不开、稀疏 ID），六条关联事件依次合并的分步动画 |
| 20 | [拓扑排序与最短路径：清算谁先谁后，换汇走哪条路](https://study.ainiya.de/algo/topo-shortest.html) | 算法基础第 18 课：Kahn 入度 + 队列和环检测、Dijkstra 为什么出堆才定下来、延迟删除、负边与 Bellman-Ford、清算依赖和换汇路线实测、五个坑（环没报警、提前定、负边、旧条目、汇率相乘），换汇图 Dijkstra 分步动画 |
| 21 | [贪心：每一步只拿眼前最好的，什么时候不会后悔](https://study.ainiya.de/algo/greedy.html) | 算法基础第 19 课：不限次数买卖吃下每段上涨、交换论证证明最早结束的先排、手续费和怪面额下贪心为什么失灵、Dijkstra 和 Huffman 里的贪心，四条排序规则对拍实验台 |
| 22 | [回溯：把所有选择走一遍，走不通就退回来](https://study.ainiya.de/algo/backtracking.html) | 算法基础第 20 课：整张吃单凑手数的决策树、做选择 / 递归 / 撤销模板、超了就停 / 剩下不够 / 同层去重三种剪枝、存引用和忘撤销两个坑、Java 正则的回溯和 JDK 11 起的失败记忆，剪枝节点数实验台 |
| 23 | [动态规划入门：状态和转移，带手续费的买卖为什么贪心不行](https://study.ainiya.de/algo/dp-basics.html) | 算法基础第 21 课：回溯里的重复子问题、状态 = 决定未来的最少信息、空仓 / 持有状态机和转移、记忆化 / 递推表 / 滚动变量三种写法、冷冻期多一个状态、更新顺序和起点两个坑，手续费与交易笔数实验台 |
| 24 | [动态规划进阶：背包和序列，一笔资金分给几个策略](https://study.ainiya.de/algo/dp-knapsack.html) | 算法基础第 22 课：资金分策略的 0-1 背包、一维为什么倒序、完全背包凑钱和组合 / 排列计数、编辑距离做交易对纠错、O(nW) 伪多项式和预算粒度，分资金实验台 |
| 25 | [字符串：KMP 与 Trie，输入 BT 就补全交易对](https://study.ainiya.de/algo/kmp-trie.html) | 算法基础第 23 课：Trie 节点即前缀、补全实测对比全表扫 / TreeMap 区间 / Trie、KMP 失配时主串不退、next 数组即最长相等前后缀、JDK indexOf 的朴素实现和最坏输入，朴素与 KMP 比较次数实验台 |
| 26 | [设计题：LRU、LFU 与限流，行情快照缓存和每账户每秒 20 单](https://study.ainiya.de/algo/lru-lfu-limit.html) | 算法基础第 24 课：手写 LRU（哈希表 + 双向链表）和 O(1) LFU（次数桶 + minFreq）、懒补充令牌桶和账户表淘汰、LRU 怕扫描 LFU 怕热点漂移的实测，三种淘汰策略命中率实验台 |
| 27 | [题型地图：看到题怎么认出用哪招，12 站换成 12 组面试题](https://study.ainiya.de/algo/problem-map.html) | 算法基础第 25 课：规模定复杂度、信号词表、按不变式认题的六类地图、12 站对应的 LeetCode 题、1801 积压订单就是撮合、本机每秒能跑多少次，14 题看题认招实验台 |
| 28 | [位运算与逻辑运算：订单标志位、1 亿账户打卡和移位的坑](https://study.ainiya.de/algo/bit-ops.html) | 算法基础第 1 课补充：& \| ^ ~ 和三种移位、掩码四件套（置位 / 清位 / 翻转 / 测试）、逻辑运算的短路、x&(x−1) 和 lowbit 等技巧、EnumSet / BitSet / HashMap 源码里的位运算、六个实测的坑，32 位计算器实验台 |
| 29 | [原码、反码、补码：负数在机器里怎么存，减法为什么能变成加法](https://study.ainiya.de/algo/signed-codes.html) | 算法基础第 1 课补充，零基础讲：为什么要约定、原码为什么加不对、三者怎么从 +x 一步步变出来、16 格钟面上减 3 等于加 13、反码 = 15 − x 和补码 = 16 − x 的名字来历、Java 全部 int 验证 -x == ~x + 1、double 的 −0.0，三种码对照加法器实验台 |
