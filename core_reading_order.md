# 核心阅读顺序

这份顺序以“跨系统微服务诊断与修复迁移”方法设计为目标，不按发表时间排序。

## 第一组：先确定问题边界

1. **OpenRCA 2.0**：确认跨系统 RCA 和过程级因果标注已经出现，不能主张“首个跨系统 RCA benchmark”。
2. **A Multi-Dataset Benchmark for Evaluating LLM Agents in Microservice Failure Diagnosis**：理解跨数据集、定位—识别—理由三层评测。
3. **R2Act / Can LLMs Really Recover Microservice Failures?**：确认“诊断正确”与“修复动作有效”之间存在独立缺口。
4. **Beyond Fault Localization / DiagGuard**：理解最终答案正确仍可能缺少证据路径，支持轨迹级评测。
5. **EviRCA**：最接近“系统无关证据提取 + 推理”的新工作，需要作为直接竞争者。

## 第二组：判断 harness 与 skill 迁移还能主张什么

6. **PolySkill**：抽象目标与具体实现解耦已被提出，简单的 core/adapter 分层不足以构成创新。
7. **ContractSkill**：显式前置条件、后置条件、恢复规则、验证和局部修复均已有直接近邻。
8. **SkillMigrator**：跨站点结构匹配、动态 grounding 和回退已有实现。
9. **Meta-Harness**：允许直接搜索整个 harness，是必须同预算比较的通用强基线。
10. **Agentic Harness Engineering (AHE)**：把 harness 组件、执行经验和编辑决策都变成可观测对象，最接近自动演化叙事。
11. **Continual Harness**：覆盖单次长程运行内的在线、无重置 harness 自适应。
12. **SkillHone**：覆盖跨会话的 skill 修订历史与评测证据持久化。
13. **Do Agent Optimizers Compound?**：说明持续优化必须显式控制回归，否则一次性提升不能稳定累积。

## 第三组：形成微服务场景特有的方法约束

14. **TORAI**：处理 tracing 缺失和拓扑盲点，说明目标系统的观测结构本身可能不完整。
15. **ORCA**：把遥测诊断连接到代码/配置补丁，并区分多层修复验证。
16. **STRATUS**：提供事务性执行、回滚与 no-regression 基础设施，不宜把这些单独包装成主创新。
17. **SREGym、ITBench、AIOpsLab**：用于设计可执行、在线、可比较的 agent 评测环境。
18. **Few-Shot Cross-System Anomaly Trace Classification**：直接展示跨系统适配可行，但任务仍局限于 trace 分类。
19. **RCAEval、RCD、DiagFusion、MicroHECL**：构成传统多模态、因果和工业 RCA 强基线。

## 第四组：支撑形式化叙事

20. **Transportability of Causal and Statistical Relations**：用 selection diagram 表达源域与目标域的稳定部分和变化部分。
21. **Meta-Transportability of Causal Effects**：解释如何从多个源环境融合可迁移证据。
22. **Transportability from Multiple Environments with Limited Experiments**：为有限目标试验和可辨识性提供理论参照。

读完前三组后，方法主张应聚焦为：**在目标系统试验昂贵且遥测/工具/拓扑均可能变化时，如何利用区分性探测识别源 harness 与 skill 中失效的前提，并以最少目标交互完成可验证、可回归控制的联合迁移。** “自动提炼 skill”“把实现替换成 adapter”“用反思改 prompt”本身都不足以形成新颖性。
