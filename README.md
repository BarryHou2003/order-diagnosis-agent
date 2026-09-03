<div align="center">

# Order Diagnosis Agent

**一句客诉进，一份诊断出。**

面向直播电商投流场景的订单诊断 Agent —— 听懂广告主在问什么，用数据完成归因，给出可执行的建议，并打通赔付闭环。

[![Website](https://img.shields.io/badge/Website-Live%20Demo-2f5cff?style=flat-square)](https://barryhou2003.github.io/order-diagnosis-agent/)
![Status](https://img.shields.io/badge/Status-In%20Production-34d399?style=flat-square)
![Model](https://img.shields.io/badge/Model-Qwen3--14B%20%C2%B7%20Local-7c3aed?style=flat-square)
![Coverage](https://img.shields.io/badge/Complaint%20Coverage-88.59%25-06b6d4?style=flat-square)

</div>

---

## Why

直播电商投流的每一笔异常消耗背后，都是一个等待回答的广告主：

> 「只成交一单，为什么扣了我 3000 元？」

一次人工排查要跨多个看板取数，耗时约 **30 分钟**；而模版式回复没有归因、没有数据、没有赔付结论。本系统把这件事变成一条分钟级的自动化诊断链路：

```
广告主客诉 ──▶ 意图理解 ──▶ 诊断引擎 ──▶ 场景路由 ──▶ 报告生成 ──▶ 赔付闭环
             （诉求拆解 ·    （成本 / 跑量 /   （A–H 场景 ·     （槽位化单 Agent ·  （标准赔付 +
              事实核验 ·      流速规则库 ·      诊断与决策        本地 Qwen3-14B）    异常赔付二次判断）
              LTR 排序）      显著性检验）      分离）
```

## Key Design Decisions

| # | 决策 | 一句话 |
|---|------|--------|
| 01 | **意图识别与诉求排序** | 规则 + 小模型分类 + BM25 正反例召回，LTR 排序主诉优先级 —— 先听懂，再回答 |
| 02 | **槽位化报告生成** | 把自由写作变成槽位填充，格式与口径由结构约束 —— 小参数本地模型上的对照实验中胜过多 Agent 方案 |
| 03 | **诊断与决策分离** | A–H 场景路由：冲突结论统一裁决，未授权建议自动过滤 |
| 04 | **三层评测体系** | 确定性规则 + LLM Judge + 人工复核 —— 每个架构决策都有可复现的评测口径 |

## Results

- **88.59%** 客诉问题覆盖率（from ~10.5%）
- **< 1 min** 单笔诊断耗时（from ~30 min 人工排查）
- **637h+ / 年** 人力时间释放（年化估算）
- **7 × 24** 全时段在线，双端上线（企微 Bot + 网页端）

全部能力运行在本地部署的开源模型之上 —— 数据不出域，成本可控。

## Live

完整的交互式项目展示（真实案例、架构细节、落地情况）：

**[barryhou2003.github.io/order-diagnosis-agent](https://barryhou2003.github.io/order-diagnosis-agent/)**
