# Router v1.0 · 2026-11-22

固定段。开工必读，先于检索（protocol 1.0）。冲突优先级：用户当次指令 >
本文件 > 任务卡 > protocol 默认段 > skills/ 内部规则。

## 1. 路由纪律

1.1 先判后检索：未输出路由块不得发起任何检索。
1.2 禁改判：路由块输出后不得同任务内静默改判 task_class；判错 →
    停下声明改判原因，重发路由块，按 protocol 1.10 四步重检工件。
1.3 信心低 → 用通用卡（无 _commercial/_research 后缀的任务卡）。
1.4 路由块即复述留档：输出即留痕，不另存文件。
1.5 杂糅单会话：路由块给拆分计划，逐段执行，段间读上段交付物；
    B+D / C+D 计划必标"人审"节点，到点即停。

## 2. 路由块格式

块内只许含判别字段，禁含执行内容（protocol 1.15d）：

- a) task_class：A/B/C/D（杂糅标组合 + 拆分计划）
- b) 领域与版本：商用 / 研究 / 通用 → 选用对应 protocol 版与任务卡
- c) 计划：子面拆分 + skill 挂载声明（§3：挂载哪个/跳过哪个/理由一句）
- d) 依据：一句判别理由（看动词：收集→A，分析→B，设计→C，建议→D）
- e) 信心：高/中/低
- 附加：目标锁定句（ABA 锚，protocol 1.14c）；偏离声明
  （protocol 1.16：偏离项 + 场景理由 + 替代值）

## 3. 任务类型 → 任务卡 → skill 路由表

判序：先定 task_class（d 依据）→ 查本表定任务卡与 skill →
路由块 c) 声明挂载决定。skills/ 目录与登记见 skills/_registry.md。

| 触发（任务类型 / 子面） | 任务卡 | 挂载 skill | 强度 |
|---|---|---|---|
| A 收集（默认） | task_card_A_v4 | —（直接检索） | — |
| A 收集：含"舆情/反馈/讨论/反响"子面 | task_card_A_v4 | news-radar-cn | 按需·仅线索层 |
| A 收集：来源身份或真实性存疑 | task_card_A_v4 | source-verification | 按需 |
| B 分析（默认） | task_card_B_v4 / B_commercial / B_research | source-verification（关键 L1 入库前） | 强制·关键证据 |
| B 分析：结论将对外引用或进决策 | 同上 | fact-check-workflow（关键结论逐条） | 强制·关键结论 |
| C 设计 | task_card_C_v4 | —（涉事实断言回 B 流程核查） | — |
| D 建议 | task_card_D_v4 / D_commercial / D_research | fact-check-workflow（依据链全量） | 强制 |
| 任意类：社媒/平台反馈面 | 对应卡 | social-media-intelligence | 按需·仅线索层 |
| 任意类：图片/视频/文件/合成媒体真伪 | 对应卡 | source-verification | 按需 |

## 4. skill 使用规则

4.1 方法是方法，证据是证据：挂载 skill 不改变证据分级
    （protocol 4.x）；skill 产出（评级、协调分、聚类结果）默认
    observation·confidence L，升级须独立 L1 佐证。
4.2 线索层纪律：news-radar-cn 与 social-media-intelligence 的产出
    仅作线索；写入 findings/ 或 digest/ 前必须回到一手来源核验，
    未核验不得入板、不得作为 L1/L2 的 sources。
4.3 强制项豁免：声明"无关键新证据 / 无关键结论"可跳过对应强制
    skill，路由块或 temp 留痕一句理由；事后出现关键结论须补做。
4.4 冲突：skill 内部规则与 protocol/router/任务卡冲突 → 以
    protocol 与 router 为准（承重结构不可被 skill 覆盖）。
4.5 凭证制延伸（protocol 1.15）：声明"已用某 skill"须附其产出物
    路径（claim log / 核验记录 / 评级表 / 线索卡）；无产出物 =
    未执行，不得假装执行。
4.6 第三方 skill 安全：新 skill 入库走 skill-finder 流程
    （skills/skill-finder 规范：安全审查三条件全过才可用）；
    已入库 skill 复用前过 REVIEW.md 时效检查。
