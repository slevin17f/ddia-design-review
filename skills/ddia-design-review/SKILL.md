---
name: ddia-design-review
description: |
  依据 Martin Kleppmann《数据密集型应用系统设计》评审数据架构。用户给出访问模式、复制或分片方案、并发历史、批流管道或跨系统写入时，推演故障和重试，比较候选保证，交付有来源的验收案例。
metadata:
  cangjie.generated-by: cangjie-tools v2.5.0
  cangjie.variant: single
  cangjie.bundle-id: bundle.ddia-design-review
  cangjie.capability-count: 12
  cangjie.entrypoint-count: 1
---
# 数据密集型应用系统设计（2018 年中译本） — 全书能力入口

## 触发与不触发

**适用**：与本书能力域相关的咨询与任务（见下方路由表的意图列）。
**不适用**：
- 产品版本默认配置、实测性能与生产环境操作需另行取证。

## 核心原则（常驻速览，概览类问题读到这里即可回答）

1. 先复述用户最关心的一次操作、负载分布与必须始终成立的业务条件。给证据标明来源，把补设的数字写成假设。
2. 按意图选主卡；问题跨组件时再读表内关联卡。例如订单已提交却未进入索引，先查端到端，再查流处理。
3. 写出最短的操作历史：谁在何时读、写、确认、重试，哪些结果合法。用它比较现方案和一个备选，标出延迟、可用性、成本和运维代价。
4. 给出决定、成立条件、能推翻它的输入和可复演的验收标准。引用章及 PDF 物理页。

## 能力路由（先读本表，按意图加载 1 张能力卡）

| 用户意图 | 先读 | 补读/备注 |
|---|---|---|
| 建立负载与服务目标（扇出 / 负载 / p99 / 容量） | references/capabilities/workload.md | references/capabilities/storage.md、references/capabilities/partition.md |
| 由访问路径选择数据模型（连接 / 文档 / 图遍历 / 局部性） | references/capabilities/model.md | references/capabilities/storage.md、references/capabilities/evolution.md |
| 选择存储与索引结构（LSM / B树 / 压实 / 列存 / OLAP） | references/capabilities/storage.md | references/capabilities/workload.md、references/capabilities/model.md |
| 验证新旧读写兼容性（模式演化 / 编码 / 滚动升级 / 回滚） | references/capabilities/evolution.md | references/capabilities/model.md、references/capabilities/stream.md |
| 选择复制与会话保证（主从 / 复制延迟 / 仲裁 / 读己之写） | references/capabilities/replication.md | references/capabilities/faults.md、references/capabilities/consensus.md |
| 估算热点和跨分区成本（分片 / 热点 / 二级索引 / 再平衡） | references/capabilities/partition.md | references/capabilities/workload.md、references/capabilities/replication.md |
| 验证事务隔离能否保持不变量（写倾斜 / 快照隔离 / 幻读 / 串行化） | references/capabilities/transactions.md | references/capabilities/consensus.md、references/capabilities/end-to-end.md |
| 判断超时与过期持有者（租约 / 超时 / 时钟 / 进程暂停 / 栅栏） | references/capabilities/faults.md | references/capabilities/consensus.md、references/capabilities/end-to-end.md |
| 界定顺序和协调范围（线性一致性 / 共识 / 全序广播 / 两阶段提交） | references/capabilities/consensus.md | references/capabilities/transactions.md、references/capabilities/faults.md |
| 设计可重跑的批计算（批处理 / 连接 / 倾斜 / 重算） | references/capabilities/batch.md | references/capabilities/storage.md、references/capabilities/stream.md |
| 处理乱序、重放和重复交付（事件时间 / CDC / 窗口 / 偏移量） | references/capabilities/stream.md | references/capabilities/batch.md、references/capabilities/end-to-end.md |
| 审阅跨系统正确性与数据责任（双写 / 请求去重 / 对账 / 数据删除 / 隐私） | references/capabilities/end-to-end.md | references/capabilities/transactions.md、references/capabilities/stream.md |

**非能力类查询**：
- 书名/作者/章节/整书概览 → references/overview.md
- 术语解释 → references/glossary.md
- 决策规则速查（不需要原文依据时） → references/cheatsheet.md
- 完整意图与关键词索引（本表未覆盖的意图先查这里） → references/capability-index.md

## 加载规则

- 每次任务先读本文件，再按路由表加载 **1** 张能力卡；任务明确跨域时最多加载 2 张。
- 概览/书名类问题不加载能力卡，用「核心原则」与 overview.md 回答。
- 路由表与 capability-index.md 都无法命中的意图，明确告知超出本书范围，不要硬套。

## 边界与判停

- 只有系统名字时先索取一个读写路径和一个不可接受的结果。
- 具体产品行为依赖版本、部署和配置，缺失时把判断标为条件性并列出验证办法。
