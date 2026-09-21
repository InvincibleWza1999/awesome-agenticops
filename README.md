# 跨系统微服务诊断与修复迁移：本地文献库

检索截止日期：**2026-09-21**。

本目录围绕以下研究问题收集论文：如何从已有系统的可观测性 harness 与运维 skill 出发，在目标系统的拓扑、遥测语义、工具接口、故障分布和修复约束发生变化时，自动识别可迁移部分、改写不兼容部分，并通过目标系统中的可执行证据验证诊断与修复。

## 内容概览

| 目录 | 数量 | 页数 | 大小 | 收录范围 |
|---|---:|---:|---:|---|
| `method/` | 30 | 740 | 99.48 MB | harness 自动优化、skill 归纳/迁移/修复、持续学习、工作流搜索、因果可迁移性与领域泛化 |
| `microservice/` | 29 | 540 | 46.39 MB | 微服务/SRE/云运维的诊断、RCA、修复、可观测性与交互式 benchmark |
| **合计** | **59** | **1280** | **145.87 MB** | 26 篇已同行评审或已接收稿，33 篇预印本 |

按与当前选题的关系，清单中另标注了 35 篇 `core`、15 篇 `direct` 和 9 篇 `background`。

## 文件与清单

- `manifest.csv`：完整索引。包含分类、题名、第一作者、年份、venue、发表状态、相关性、主题、落地页、PDF 原始地址、本地文件名、字节数、页数和 SHA-256。
- `excluded_sources.csv`：检索命中但不应进入有效语料库的条目及原因。
- `corpus_seed.json`：可复现下载清单。
- `download_corpus.py`：下载和校验脚本。已存在且校验有效的 PDF 不会重复下载。
- `core_reading_order.md`：围绕论文设计问题安排的优先阅读顺序。

所有 59 个 PDF 均通过以下检查：文件头为 `%PDF-`、文件大小至少 20 KB、`pdfinfo` 可读取页数、SHA-256 已写入清单。当前 `download_failures.csv` 只有表头，表示没有未解决的下载失败。

## 检索与筛选方法

检索覆盖 ICLR、ICML、NeurIPS、MLSys、ACL、COLM、ICSE、FSE、APSys、AAAI、AISTATS、ACM Computing Surveys、IEEE Transactions on Services Computing、PMLR、OpenReview、ACL Anthology 和 arXiv。优先下载正式论文集版本；正式版本不可稳定获取时，使用作者公开稿或 arXiv 版本。

检索词由四组概念交叉构成：

1. `agent harness`、`harness optimization/evolution`、`workflow generation/search`；
2. `agent skill induction/evolution/repair/transfer`、`continual agent learning`；
3. `microservice/SRE/cloud operations` 与 `root cause analysis/diagnosis/remediation/recovery/observability`；
4. `cross-system/cross-environment/domain generalization/causal transportability`。

纳入标准是论文至少直接支持一个关键环节：harness 或 skill 的表示与更新、跨环境绑定与迁移、目标侧主动探测、诊断过程证据、从诊断到修复、修复验证、或跨系统评测。经典论文只在提供不可替代的形式化基础或强基线时保留。

本目录不是整个 AIOps 或通用 agent 文献的穷尽集合。纯异常检测、通用工具调用、通用记忆、与迁移无关的提示工程，以及没有微服务/云运维实证的普通自动修复论文被排除，以避免稀释当前研究问题。

## 发表状态说明

`publication_status=peer-reviewed` 表示已在正式会议或期刊页面核实；`preprint` 表示截至检索日仅按公开预印本处理。预印本结果需要在写作时明确标注，不应与正式发表证据等同。

`Scaling Coding Agents via Atomic Skills` 没有放入 PDF 语料库。arXiv 页面显示作者因数据中的重大错误影响结果有效性而撤稿，且官方不再提供 PDF。该条目及官方页面保存在 `excluded_sources.csv`。

## 复现下载

在本目录运行：

```powershell
python .\download_corpus.py
```

脚本会重新生成 `manifest.csv` 和 `download_failures.csv`，并只下载缺失或校验失败的文件。
