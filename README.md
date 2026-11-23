# 数学笔记

个人数学学习笔记，提供 PDF 和 LaTeX 源码。

## 目录

| 目录 | 内容 |
| --- | --- |
| `TexNote/algebra/` | Hungerford《代数》自学笔记，目前包含 1.1–1.9、2.1–2.5 节 |
| `TexNote/real_analysis/` | 实变函数笔记，当前仅有模板，尚未整理正文 |
| `pdf/` | 可直接阅读或下载的 PDF |
| `.vscode/` | VS Code 编译与预览配置 |

## 阅读与下载

- [代数学笔记 PDF](pdf/algebra.pdf)
- [实变函数模板 PDF](pdf/real_analysis.pdf)

如需下载全部文件，点击仓库页面的 **Code → Download ZIP**，或运行：

```sh
git clone https://github.com/benben-cd/math_notes.git
```

## 编译源码

安装包含 XeLaTeX 和 latexmk 的 TeX 发行版（如 TeX Live），并确保编译工具已加入 PATH。

进入对应科目目录，例如 `TexNote/algebra/`，运行：

```sh
latexmk -xelatex -synctex=1 -interaction=nonstopmode -halt-on-error -file-line-error -outdir=build main.tex
```

生成的 PDF 位于该科目的 `build/main.pdf`。

使用 VS Code 时，可安装 LaTeX Workshop 扩展并打开仓库目录；打开对应科目的 `main.tex`，按 `Ctrl+Alt+B` 编译，按 `Ctrl+Alt+V` 预览。
