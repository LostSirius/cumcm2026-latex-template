<p align="center">
  <img src="assets/banner.png" alt="CUMCM 2026 LaTeX Template" width="100%">
</p>

<p align="center">
  <img alt="XeLaTeX" src="https://img.shields.io/badge/engine-XeLaTeX-008080">
  <img alt="TeX Live 2025" src="https://img.shields.io/badge/TeX%20Live-2025%2B-3D6117">
  <img alt="Overleaf" src="https://img.shields.io/badge/Overleaf-ready-47A141">
  <img alt="CUMCM 2026" src="https://img.shields.io/badge/CUMCM-2026-1F4E79">
</p>

# CUMCM 2026 LaTeX 论文模板

面向 2026 年全国大学生数学建模竞赛的非官方 LaTeX 论文模板。项目提供可直接填写的正式论文骨架、2026 年 AI 工具使用声明、支撑材料清单和独立的 AI 工具使用详情模板，并兼容本地 TeX Live 与 Overleaf。

> [!IMPORTANT]
> 本项目不是全国大学生数学建模竞赛组委会官方模板，不代表组委会或任何赛区认可。提交前必须以[官网最新通知](https://www.mcm.edu.cn/)和所在赛区要求为准。

## 主要特性

- 默认生成电子版论文：无承诺书、无编号专用页，第一页直接为摘要。
- A4 纸，四边页边距 2.5 cm，摘要页从页码 1 开始。
- 不生成目录；AI 工具使用声明固定放在参考文献之前。
- 提供问题重述、模型假设、符号说明、分问求解、检验、评价和附录骨架。
- 附录预留支撑材料文件列表和完整源程序位置。
- 提供独立的 `AI工具使用详情.tex`，用于生成支撑材料中的说明 PDF。
- Windows 优先使用 Times New Roman/Arial；Overleaf/Linux 自动回退到 TeX Gyre 字体。
- 使用 `listings` 展示代码，无需 Python、Pygments 或 `shell-escape`。

## 2026 年硬性规范速查

以下内容来自《全国大学生数学建模竞赛论文格式规范（2026年修订稿）》：

1. 白色 A4 纸，上下左右页边距均不少于 2.5 cm。
2. 电子版不得包含承诺书和编号专用页，第一页必须是摘要专用页。
3. 摘要包含标题和关键词，无需英文翻译，原则上不超过一页。
4. 页码从摘要页起，以阿拉伯数字 `1` 开始，位于页脚中部。
5. 正文不要目录；从摘要结束后到附录之前不超过 30 页，参考文献计入。
6. 无论是否使用 AI，都须在参考文献之前写明 AI 工具使用声明。
7. 附录必须列出支撑材料文件，并包含全部完整、可运行的源程序。
8. 摘要、正文、附录和支撑材料不得出现队员、学校、赛区等身份信息。
9. 论文为单个 PDF 或 Word 文件，建议 PDF，不超过 20 MB，不要压缩。
10. 支撑材料为一个 RAR 或 ZIP 文件，不超过 20 MB。

字体、字号、行距和颜色未被全国规范统一限定。本模板采用清晰、保守的科技论文排版。

相关文件：

- [论文格式规范（2026年修订稿）](https://www.mcm.edu.cn/html_cn/node/4cd596519c9eb9fbd866398f6df0caa3.html)
- [人工智能工具使用规定（2026年试行）](https://www.mcm.edu.cn/html_cn/node/fef94648f2836ab6cc81586f4c38512b.html)

## 目录结构

```text
.
├── paper.tex                  # 正式论文主文件
├── AI工具使用详情.tex         # 使用 AI 时单独编译并放入支撑材料
├── cumcmthesis.cls            # 文档类（派生自上游 CUMCMThesis）
├── cumcm2026.sty              # 2026 年补充样式
├── latexmkrc                  # latexmk / Overleaf 编译配置
├── figures/                   # 论文图片
├── assets/                    # README 项目视觉资源
├── README.md
├── NOTICE.md
└── CHANGELOG.md
```

## Overleaf 使用

1. 在 GitHub 项目页选择 **Code → Download ZIP**。
2. 登录 [Overleaf](https://www.overleaf.com/)。
3. 选择 **New Project → Upload Project**，上传整个 ZIP。
4. 在 **Menu** 中将 **Main document** 设为 `paper.tex`。
5. 将 **Compiler** 设为 **XeLaTeX**，然后点击 **Recompile**。

仓库根目录的 `latexmkrc` 已指定 XeLaTeX；若 Overleaf 没有自动识别，手动设置一次即可。不要使用 pdfLaTeX。

共享协作时，点击 Overleaf 右上角 **Share**，使用邮件邀请或创建可编辑链接。建议三名队员分工编辑不同章节，合并前统一检查符号、单位和引用。

## 本地使用

推荐 TeX Live 2025 或更新版本：

```bash
git clone <本仓库的 HTTPS 地址>
cd cumcm2026-latex-template
latexmk -xelatex paper.tex
```

清理编译产物：

```bash
latexmk -C paper.tex
```

Windows PowerShell、Linux 和 macOS 的命令相同。中文源文件统一使用 UTF-8 编码。

## 开始写论文

只需编辑 `paper.tex`：

```tex
\title{论文题目}

\begin{abstract}
概括背景、模型、方法和主要数值结论……
\keywords{关键词1 \quad 关键词2 \quad 关键词3}
\end{abstract}
```

正式提交的电子版必须保留：

```tex
\documentclass[withoutpreface,bwprint]{cumcmthesis}
```

`withoutpreface` 会移除承诺书和编号专用页。只有在所在赛区明确需要纸质版时，才可另行生成带封面的版本；带封面的 PDF 不能作为电子作品提交。

### 插入图片

将图片放入 `figures/`：

```tex
\begin{figure}[htbp]
  \centering
  \includegraphics[width=0.72\textwidth]{result.png}
  \caption{模型计算结果}
  \label{fig:result}
\end{figure}
```

图题放在图下方，表题放在表上方；正文使用 `图~\ref{fig:result}` 引用。

### 公式与符号

```tex
\begin{equation}
  \min_{\bm{x}} f(\bm{x})
  \quad \text{s.t.}\quad
  g_j(\bm{x})\leq 0.
\end{equation}
```

所有变量应在首次出现处或符号表中定义，保持单位、上下标和向量记法一致。

### 参考文献

模板默认使用无需额外工具的 `thebibliography`。正文中引用：

```tex
已有研究提出了相关方法\cite{reference-key}。
```

参考文献条目：

```tex
\bibitem{reference-key}
作者. 文献题目[J]. 期刊, 年, 卷(期): 页码.
```

引用网页、公开数据、他人算法或源码时，也必须列出来源并在正文标注。

## AI 工具使用声明

声明必须位于参考文献之前，以下两种情况只能保留一种。

未使用 AI：

```tex
\CumcmAINotUsed
```

使用了 AI：

```tex
\CumcmAIUsed{语言润色、代码调试}
```

使用 AI 时，还须编译：

```bash
latexmk -xelatex "AI工具使用详情.tex"
```

将生成的 `AI工具使用详情.pdf` 放进支撑材料压缩包，不要放进论文正文。详情须写明：

1. 工具名称、版本或型号；
2. 具体使用目的和环节；
3. 主要提示方式和使用过程；
4. 对输出的采纳、人工修改与核验情况。

核心建模与分析必须由参赛队主导，所有 AI 输出须逐项人工审查和复核。

## 附录与支撑材料

论文附录须列出支撑材料中的文件，并粘贴建模所用的全部完整、可运行源程序。源文件还须以原格式再放入支撑材料。

支撑材料通常包括：

- 全部可运行源程序；
- 自主查阅或整理的数据，不含赛题直接提供的原始数据；
- 较大篇幅的中间结果、图表和必要参考资料；
- `AI工具使用详情.pdf`（仅使用 AI 时）。

若确实没有程序，应在附录写明“本论文没有用到程序”；若确实没有支撑材料，应写明“本论文没有支撑材料”。

## 匿名与隐私

提交前同时检查源文件、PDF、图片、压缩包和文件属性：

- 不写队员姓名、学校、学院、赛区、队号、手机号或邮箱；
- 不使用含姓名的文件名、目录名或图片水印；
- 删除 Word/Excel/PDF 的作者、公司和最后保存者元数据；
- 截图应裁掉账号头像、系统用户名和本地文件路径；
- PDF 属性中的 Author 应为空；
- 生成 MD5 后不要再次打开或保存参赛文件，否则校验值会变化。

本仓库示例不含真实身份数据，PDF 元数据的作者字段也被留空。

## 提交前检查清单

- [ ] PDF 第一页是题目、摘要和关键词，且摘要原则上不超过一页
- [ ] 没有承诺书、编号专用页和目录
- [ ] 页码从摘要页的 1 开始并位于页脚中部
- [ ] 摘要后至附录前不超过 30 页
- [ ] AI 声明位于参考文献之前，且只保留一种
- [ ] 使用 AI 时已准备 `AI工具使用详情.pdf`
- [ ] 所有引用均在正文标注并列入参考文献
- [ ] 附录含支撑材料清单和完整可运行程序
- [ ] 程序本地完整运行，结果与论文一致
- [ ] 所有文件、属性、图片和压缩包均无身份信息
- [ ] 论文 PDF 与支撑材料分别不超过 20 MB
- [ ] 最终文件与已提交 MD5 完全一致

## 常见问题

### Overleaf 报 `font not found`

确认编译器为 XeLaTeX。文档类会在 Windows 字体不可用时自动回退到 TeX Gyre 字体，中文使用 TeX Live 自带的 Fandol 字体。

### 摘要超过一页

优先压缩背景和过程描述，保留每问的核心方法、关键结果与结论。不要通过缩小页边距规避限制。

### 是否需要目录或英文摘要

不需要。2026 年规范明确要求正文不要目录，摘要无需翻译成英文。

### 为什么没有提交编译后的 PDF

PDF 是源文件的构建产物，仓库只维护可审查的源文件。GitHub Actions 和 Overleaf 均可自动编译。

## 来源与声明

本仓库是 [latexstudio/CUMCMThesis](https://github.com/latexstudio/CUMCMThesis) 的派生版本，保留 GitHub Fork 关系和上游提交历史。主要改动包括正式论文骨架、2026 年 AI 说明、Overleaf 字体回退、隐私检查指南和自动编译配置。

上游仓库当前未提供明确的许可证文件，本仓库因此不擅自附加新的软件许可证。使用、修改和再分发前，请自行确认上游作者授权及适用规则。详见 [NOTICE.md](NOTICE.md)。
