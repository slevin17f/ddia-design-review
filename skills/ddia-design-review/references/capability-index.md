# 能力索引（完整版）

| capability_id | 标题 | 重要度 | 意图 | 关键词 | 能力卡 |
|---|---|---|---|---|---|
| cap.ddia.workload | 建立负载与服务目标 | high | 建立负载与服务目标（扇出 / 负载 / p99 / 容量） | 扇出、负载、p99、容量 | capabilities/workload.md |
| cap.ddia.model | 由访问路径选择数据模型 | high | 由访问路径选择数据模型（连接 / 文档 / 图遍历 / 局部性） | 连接、文档、图遍历、局部性 | capabilities/model.md |
| cap.ddia.storage | 选择存储与索引结构 | high | 选择存储与索引结构（LSM / B树 / 压实 / 列存 / OLAP） | LSM、B树、压实、列存、OLAP | capabilities/storage.md |
| cap.ddia.evolution | 验证新旧读写兼容性 | high | 验证新旧读写兼容性（模式演化 / 编码 / 滚动升级 / 回滚） | 模式演化、编码、滚动升级、回滚 | capabilities/evolution.md |
| cap.ddia.replication | 选择复制与会话保证 | high | 选择复制与会话保证（主从 / 复制延迟 / 仲裁 / 读己之写） | 主从、复制延迟、仲裁、读己之写 | capabilities/replication.md |
| cap.ddia.partition | 估算热点和跨分区成本 | high | 估算热点和跨分区成本（分片 / 热点 / 二级索引 / 再平衡） | 分片、热点、二级索引、再平衡 | capabilities/partition.md |
| cap.ddia.transactions | 验证事务隔离能否保持不变量 | high | 验证事务隔离能否保持不变量（写倾斜 / 快照隔离 / 幻读 / 串行化） | 写倾斜、快照隔离、幻读、串行化 | capabilities/transactions.md |
| cap.ddia.faults | 判断超时与过期持有者 | high | 判断超时与过期持有者（租约 / 超时 / 时钟 / 进程暂停 / 栅栏） | 租约、超时、时钟、进程暂停、栅栏 | capabilities/faults.md |
| cap.ddia.consensus | 界定顺序和协调范围 | high | 界定顺序和协调范围（线性一致性 / 共识 / 全序广播 / 两阶段提交） | 线性一致性、共识、全序广播、两阶段提交 | capabilities/consensus.md |
| cap.ddia.batch | 设计可重跑的批计算 | high | 设计可重跑的批计算（批处理 / 连接 / 倾斜 / 重算） | 批处理、连接、倾斜、重算 | capabilities/batch.md |
| cap.ddia.stream | 处理乱序、重放和重复交付 | high | 处理乱序、重放和重复交付（事件时间 / CDC / 窗口 / 偏移量） | 事件时间、CDC、窗口、偏移量 | capabilities/stream.md |
| cap.ddia.end-to-end | 审阅跨系统正确性与数据责任 | high | 审阅跨系统正确性与数据责任（双写 / 请求去重 / 对账 / 数据删除 / 隐私） | 双写、请求去重、对账、数据删除、隐私 | capabilities/end-to-end.md |
