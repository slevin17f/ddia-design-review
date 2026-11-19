# DDIA 数据架构评审 Skill

把一个架构选择写成可复演的判断。输入业务约束和一段读写过程，Skill 会给出最短的失败时序、两个设计选择各自成立的条件，以及可观察的验收结果。依据 Martin Kleppmann《数据密集型应用系统设计》2018 年中译本整理，内含 12 张中文能力卡。

## 安装到 Codex

在终端执行以下命令。重新开启会话后，可用 `$ddia-design-review` 调用。

```sh
git clone https://github.com/slevin17f/ddia-design-review.git
mkdir -p ~/.agents/skills
cp -R ddia-design-review/skills/ddia-design-review ~/.agents/skills/
```

## 试一次评审

> 用 $ddia-design-review 评审订单列表。创建订单后返回成功，列表从异步副本读取。有人刷新后没看见订单，再点了一次下单。请画出可能的读写时序，区分可见性与重复创建，给两个验收用例。

例如，第一次创建已在主库提交，但列表所读副本还没追上。为这个用户提供写后可读可以解决可见性；响应丢失后仍需用稳定的请求标识识别第二次提交。验收时可分别让副本暂停应用日志、让客户端错过一次成功响应，观察同一意图产生的订单数。

| 手上的问题 | 可查的能力 |
| --- | --- |
| 峰值时系统哪里先超出预算？数据怎样读写与升级？ | 负载、数据模型、存储与索引、编码演化 |
| 多副本或并发操作破坏了哪项承诺？ | 复制、分区、事务、部分失效、一致性与共识 |
| 重算、晚到、重试后结果是否仍可信？ | 批处理、流处理、端到端正确性与数据责任 |

[技能入口](skills/ddia-design-review/SKILL.md) · [能力索引](skills/ddia-design-review/references/capability-index.md) · [来源与章节](skills/ddia-design-review/references/overview.md)

本仓库提供原创评审步骤与合成练习。页码对应蒸馏时使用的中文 PDF，从封面起计数；使用其他版次可按章节和主题定位。
