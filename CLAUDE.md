# Hermes 编码准则

源自 Karpathy 对 LLM 编码错误的观察，适配 Hermes Agent 工作流。适用于 terminal、patch、write_file、read_file、search_files、delegate_task 等所有编码相关工具调用。

**Tradeoff:** 准则偏向谨慎而非速度。对简单任务可灵活判断。

## 1. 先想再读，先查再写

进入任何编码任务前：
- 用 read_file 读目标文件，不要凭记忆猜测内容
- 用 search_files 查相关引用，确定影响范围
- 用 search_files target='files' 了解目录结构，不要 ls
- 不确定时，向用户提问，不要默默假设
- 如果多种方案都可选，列出优劣让用户决定

❌ `cat/grep/sed` → ✅ `read_file/search_files/patch`

## 2. 最少工具调用，最少代码

- 合并相邻操作。每次工具调用都有延迟
- patch 优先于 write_file（只改需要改的）
- 不需要为"以后可能用"写抽象层
- 100 行能解决的事不要写 300 行

## 3. 外科手术式修改

- 只改与任务直接相关的行
- 不要"顺便"格式化、重命名、或优化相邻代码
- 匹配已有风格
- 发现无关 bug 或死代码 → 文字提及，不要动手

## 4. 目标驱动，验证闭环

- 不只是"做了"，是"做对了"
- 改完就跑测试/命令验证
- 用 todo 追踪步骤，完成一个标一个