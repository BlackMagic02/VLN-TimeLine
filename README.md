# VLN Research Timeline

Vision-and-Language Navigation 研究时间线可视化网站。

包含 **94 篇论文**、**32 个里程碑**，涵盖 2017–2026 年 VLN 领域的主要进展。

## 项目结构

```
VLN-Timeline/
├── index.html          ← 网站页面（不需要修改）
├── data.json           ← 论文数据（更新这里）
├── update_papers.py    ← 论文更新工具（LLM辅助）
└── README.md
```

---

## 一、部署到 GitHub Pages（一次性，约5分钟）

### 前置条件

- 一个 GitHub 账号 → [注册](https://github.com/signup)
- 安装 Git → [下载](https://git-scm.com/downloads)

### 步骤

#### 1. 在 GitHub 上创建仓库

1. 打开 https://github.com/new
2. Repository name 填写 `vln-timeline`（或任意名称）
3. 选择 **Public**
4. **不要**勾选 "Add a README file"
5. 点击 **Create repository**

#### 2. 本地初始化并推送

打开终端（PowerShell / CMD），进入 `VLN-Timeline` 文件夹：

```powershell
cd "d:\系统文件\OneDrive\科研相关\读论文\总结\VLN-Timeline"

git init
git add index.html data.json README.md
git commit -m "初始版本：94篇VLN论文时间线"
git branch -M main
git remote add origin https://github.com/你的用户名/vln-timeline.git
git push -u origin main
```

> ⚠️ 将 `你的用户名` 替换为你的 GitHub 用户名

#### 3. 开启 GitHub Pages

1. 打开你的仓库页面 → **Settings** → 左侧 **Pages**
2. Source 选择 **Deploy from a branch**
3. Branch 选择 `main`，文件夹选择 `/ (root)`
4. 点击 **Save**
5. 等待 1-2 分钟，页面顶部会显示你的网站地址：

```
https://你的用户名.github.io/vln-timeline/
```

**部署完成！** 🎉

---

## 二、日常更新论文

### 方法 A：使用 LLM 辅助工具（推荐）

#### 安装依赖（首次）

```bash
pip install requests openai
```

#### 设置 API Key

```powershell
# Windows PowerShell
$env:OPENAI_API_KEY = "sk-你的API密钥"

# 如果使用代理/自定义API地址（可选）：
$env:OPENAI_BASE_URL = "https://你的代理地址/v1"
$env:OPENAI_MODEL = "gpt-4o"        # 默认 gpt-4o，可改为其他模型
```

#### 用法

```bash
# 自动搜索最新VLN论文（交互式审核）
python update_papers.py

# 搜索特定关键词
python update_papers.py --query "embodied large language model navigation"

# 只搜索2025年之后的论文
python update_papers.py --year 2025

# 自动模式（LLM评分≥8分直接加入）
python update_papers.py --auto

# 手动添加（输入arXiv ID）
python update_papers.py --add
```

#### 工作流示例

```
$ python update_papers.py --year 2025

============================================================
  VLN Timeline 论文更新工具
============================================================
📊 当前: 94 篇论文, 32 个里程碑

🔍 搜索 5 个关键词（年份 ≥ 2025）...

  搜索: vision language navigation embodied
    → 8 篇新论文
  搜索: VLN instruction following navigation
    → 3 篇新论文

📋 共发现 11 篇候选论文

📄 正在评估 (1/11): SomeNewPaper: A Great Method...
  🤖 LLM评分: 9/10 ★ 里程碑
  📝 首次将XX技术引入VLN，显著提升了...
  🏷️  Model, LLM/VLA
  操作: [y]加入 / [n]跳过 / [e]编辑后加入 / [q]退出 > y
  ✅ 已加入

...

🎉 完成! 新增 3 篇论文
   94 → 97 篇论文, 32 → 33 个里程碑

💡 提示: 更新后请 git add data.json && git commit && git push 部署到线上
```

### 方法 B：直接编辑 data.json

如果你不想用脚本，也可以直接编辑 `data.json`：

1. **在 GitHub 网页上**：打开仓库 → 点击 `data.json` → 点击铅笔图标 ✏️ → 编辑 → Commit
2. **在本地**：用任何文本编辑器打开 `data.json`，找到合适的 era 添加论文

添加一篇论文的模板：

```json
{
  "date": "2025-03",
  "title": "论文标题",
  "venue": "会议/期刊 2025",
  "authors": "第一作者姓 et al.",
  "description": "60-120字的中文描述，说明论文的核心贡献。<strong>关键创新</strong>可以加粗。",
  "tags": ["Model", "LLM/VLA"],
  "milestone": false,
  "paper_url": "https://arxiv.org/abs/xxxx.xxxxx",
  "project_url": "https://项目主页",
  "code_url": "https://github.com/...",
  "citations": 50,
  "affiliation": "机构名",
  "concepts": ["核心概念1", "核心概念2"]
}
```

### 方法 C：在 GitHub 上直接编辑

1. 访问 `https://github.com/你的用户名/vln-timeline`
2. 点击 `data.json`
3. 点击右上角 ✏️ 编辑图标
4. 在合适的 era 中添加新论文
5. 填写 commit message → 点击 **Commit changes**
6. GitHub Pages 会在 1-2 分钟内自动更新

---

## 三、推送更新到线上

每次本地修改 `data.json` 后：

```bash
cd "VLN-Timeline目录路径"
git add data.json
git commit -m "添加: PaperA, PaperB 等N篇新论文"
git push
```

GitHub Pages 会在 1-2 分钟内自动部署更新。

---

## 四、本地预览

由于 `index.html` 使用 `fetch()` 加载 JSON，直接双击打开会遇到 CORS 限制。
需要用本地服务器：

```bash
cd "d:\系统文件\OneDrive\科研相关\读论文\总结\VLN-Timeline"

# 方法1: Python（推荐）
python -m http.server 8080

# 方法2: Node.js
npx serve .
```

然后浏览器打开 http://localhost:8080

---

## 五、data.json 数据结构说明

```
data.json
├── eras[]                  ← 时间线分期
│   ├── name                ← 时期名称（如"基础奠基期"）
│   ├── range               ← 时间范围描述
│   ├── color               ← 主题色
│   └── papers[]            ← 该时期的论文列表
│       ├── date            ← 发表日期 "YYYY-MM"
│       ├── title           ← 论文标题
│       ├── venue           ← 会议/期刊
│       ├── authors         ← 作者（"姓 et al."格式）
│       ├── description     ← 中文描述（支持<strong>加粗</strong>）
│       ├── tags[]          ← 分类标签
│       ├── milestone       ← 是否为里程碑
│       ├── paper_url       ← (可选) 论文链接
│       ├── project_url     ← (可选) 项目主页
│       ├── code_url        ← (可选) 代码仓库
│       ├── citations       ← (可选) 近似引用量
│       ├── affiliation     ← (可选) 机构
│       └── concepts[]      ← (可选) 核心概念
├── benchmarkData           ← Benchmark 对比表数据
├── sotaSeries[]            ← SOTA 折线图数据
├── lineages[]              ← 技术演进路线数据
├── surveys[]               ← 推荐 Survey 列表
├── readingPaths[]          ← 阅读路线推荐
└── glossary[]              ← 术语表
```

### 可用的 tags

| Tag | 含义 |
|-----|------|
| `Dataset` | 数据集 / 基准 |
| `Model` | 模型架构 / 方法 |
| `Pretraining` | 预训练 |
| `Continuous Env` | 连续环境 |
| `LLM/VLA` | 大语言模型 / VLA |
| `Aerial/UAV` | 无人机导航 |
| `Zero-Shot` | 零样本 |
| `Outdoor` | 室外导航 |
| `Sim2Real` | 仿真到真实 |
| `ObjectNav` | 目标物体导航 |
| `3D Scene Graph` | 3D场景图 |
| `Multi-Modal` | 多模态 |
| `Mapping` | 语义地图 |

---

## 六、常见问题

**Q: 本地双击 index.html 打不开？**
A: 需要用本地服务器（见第四节），或部署到 GitHub Pages 后在线访问。

**Q: 推送后网站没更新？**
A: GitHub Pages 部署通常需要 1-2 分钟。检查 Settings → Pages 是否显示绿色 ✅。

**Q: update_papers.py 提示 API Key 无效？**
A: 确认 `OPENAI_API_KEY` 环境变量正确设置。如使用第三方代理，同时设置 `OPENAI_BASE_URL`。

**Q: 如何更新 Benchmark 表中的数据？**
A: 编辑 `data.json` 中的 `benchmarkData` 对象，添加新行或修改数值。

**Q: 如何添加新的 era（时期）？**
A: 在 `data.json` 的 `eras` 数组中添加新对象，参考已有 era 的格式。
