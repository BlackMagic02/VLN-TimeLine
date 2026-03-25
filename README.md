# VLN Research Timeline

**Vision-and-Language Navigation 研究时间线** — 一个交互式可视化网站，系统梳理 VLN 领域从 2017 年至今的重要论文与技术演进。

🔗 **在线访问**: [https://blackmagic02.github.io/VLN-TimeLine/](https://blackmagic02.github.io/VLN-TimeLine/)

## 概览

- **94 篇论文**，涵盖 8 个发展阶段（2017–2026）
- **32 个里程碑**论文标注
- **13 个研究方向**分类（Dataset / Model / Pretraining / LLM-VLA / Aerial-UAV / ObjectNav 等）

## 功能

| 功能 | 说明 |
|------|------|
| 时间线浏览 | 按时间分期展示论文卡片，里程碑论文高亮 |
| 多维筛选 | 多标签组合、里程碑开关、年份范围、关键词搜索 |
| 论文链接 | 一键跳转 Paper / Project / Code |
| BibTeX 导出 | 单篇复制或批量导出当前筛选结果为 `.bib` 文件 |
| Benchmark 对比 | R2R / REVERIE / VLN-CE / RxR 四大基准的可排序性能表 |
| SOTA 趋势图 | 多基准 Success Rate 历年进度折线图 |
| 技术演进图 | 6 条技术脉络的论文传承关系 |
| 论文对比 | 选择多篇论文并排对比元数据 |
| Survey 与阅读路线 | 推荐综述论文 + 入门/进阶/前沿三级阅读路径 |
| 术语表 | 20 个 VLN 核心术语解释（SR, SPL, NE, nDTW, BEV 等） |
| 引用量与机构 | 里程碑论文标注近似引用量和第一作者机构 |
| 关键概念标签 | 里程碑论文标注引入的核心技术概念 |
| 打印友好 | 支持 Ctrl+P 生成干净的打印版 |

## 涵盖的研究方向

`Dataset` `Model` `Pretraining` `Continuous Env` `LLM/VLA` `Aerial/UAV` `Zero-Shot` `Outdoor` `Sim2Real` `ObjectNav` `3D Scene Graph` `Multi-Modal` `Mapping`

## 数据来源

论文数据整理自公开学术资源（arXiv、Semantic Scholar、各会议论文集）。论文描述为人工撰写的中文摘要，旨在帮助快速理解每篇工作的核心贡献。

## 贡献

欢迎通过 Issue 或 Pull Request 补充遗漏的重要论文、修正数据错误或提出改进建议。

添加论文只需编辑 `data.json`，在对应时期的 `papers` 数组中添加条目：

```json
{
  "date": "2025-03",
  "title": "论文标题",
  "venue": "会议/期刊 2025",
  "authors": "First Author et al.",
  "description": "中文描述",
  "tags": ["Model"],
  "milestone": false,
  "paper_url": "https://arxiv.org/abs/..."
}
```

## License

MIT
