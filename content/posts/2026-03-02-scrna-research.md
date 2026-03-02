---
title: "单细胞测序 (scRNA-seq) 每日研究进展"
date: 2026-03-02
description: "单细胞测序领域最新论文与技术突破"
tags: ["单细胞测序", "scRNA-seq", "空间转录组", "研究"]
categories: ["科研进展"]
---

# 单细胞测序 (scRNA-seq) 每日研究进展报告

**日期:** 2026-03-02

---

## 📚 最近重要论文与突破

### 1. CellScope: 高性能细胞图谱工作流程
- **发表期刊:** Nature Communications
- **研究团队:** 华盛顿大学 Fred Hutchinson Cancer Center，Jessica LI 教授团队
- **核心创新:** 基于流形拟合(manifold fitting)的高性能细胞图谱构建
- **技术亮点:**
  - 采用两阶段方法：先进行基因选择以区分信号与 housekeeping 基因驱动的变异，然后去噪细胞表征以提高密切相关群体的分离度
  - 有效解决 scRNA-seq 数据中 housekeeping 基因和技术噪声带来的挑战

### 2. γδ T 细胞在动脉粥样硬化中的研究
- **发表期刊:** Genome Medicine
- **技术方法:** 整合 scRNA-seq、scTCR-seq、空间转录组学和多数据集整合
- **应用场景:** 揭示 γδ T 细胞在小鼠和人动脉粥样硬化中的分化与功能

### 3. SUM-seq: 单细胞超高通量多重染色质可及性测序
- **发表期刊:** Nature Protocols
- **作者:** Yildiz U., Lobato-Moreno S., Claringbould A. 等
- **技术突破:** 同时检测染色质可及性与基因表达的单细胞测序技术

---

## 🔧 关键技术进展

### 1. 空间转录组学整合新技术
| 技术 | 特点 | 发表 |
|------|------|------|
| **CellRefiner** | 从空间转录组重建单细胞分辨率 | Nature Communications (2026-02-27) |
| **REMAP** | 从 scRNA-seq 重建多尺度组织空间架构 | bioRxiv |
| **DANST** | 深度域对抗神经网络进行空间转录组细胞类型反卷积 | Communications Biology |

### 2. 商业化空间转录组学方案
- **Takara Bio + Illumina 合作:**
  - 整合 Trekker Single-Cell Spatial Mapping Kit 与 Illumina Single Cell 3′ RNA Prep
  - 实现高密度、高灵敏度的真正单细胞分辨率空间图谱
  - 在 AGBT 2026 会议上发布

### 3. 数据分析新方法
- **随机矩阵理论指导的稀疏PCA** (bioRxiv, 2026-02-26)
  - 解决 scRNA-seq 数据的噪声问题（扩增偏差、RNA捕获效率限制等）
- **统计功效计算:** muscat, scPower 等工具用于 scRNA-seq 功率分析

---

## 🔬 前沿应用方向

1. **肿瘤免疫研究:** 单细胞与空间转录组整合鉴定癌症预后生物标志物
2. **脑疾病研究:** 蛛网膜下腔出血的时空免疫图谱构建
3. **泛癌分析:** 整合单细胞、空间转录组与bulk测序识别OSR2作为预后和肿瘤免疫标志物

---

## 📌 今日热点总结

本周 scRNA-seq 领域的主要进展集中在:
1. **去噪与降维新算法** - CellScope 和随机矩阵理论方法
2. **空间转录组与单细胞测序的深度整合** - 多个新技术发布
3. **商业化方案推进** - Takara- Illumina 合作推动临床应用

---

*报告生成时间: 2026-03-02 08:11 GMT+8*
