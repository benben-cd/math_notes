# 数学笔记

中文手写数学笔记的 LaTeX 源码、VS Code 项目配置和转写进度。

## 内容

- `TexNote/algebra/`：代数学笔记，当前已有 1.1–1.9、2.1–2.5 节。
- `TexNote/real_analysis/`：实变函数模板，具体转写状态见该目录 `progress.md`。
- `.vscode/`：打开整个项目时使用的编译、预览和扩展推荐配置。
- `pdf/`：用于跨设备查看的最终 PDF；代数为 `algebra.pdf`，实变模板为 `real_analysis.pdf`。
- 各科目 `progress.md`：原稿照片对应关系、已处理范围、疑点和核对记录。
- `AGENTS.md` 和 `手写数学笔记转写指南.md`：AI 转写及维护约定。

原始照片通过百度网盘同步，不上传本仓库。`NotePhotos/`、`BaiduSyncdisk/`、`build/`、临时目录和本地备份均已忽略。仅将选定的最终 PDF 复制到 `pdf/` 后随源码提交。

## 换设备使用

1. 安装 Git、TeX Live 和 VS Code；VS Code 扩展可以通过 Settings Sync 同步。
2. 从 GitHub 克隆本仓库到一个空目录；已有照片目录或本地笔记时，不要直接覆盖。
3. 在 VS Code 中打开仓库根目录。若只打开某个科目，也可使用科目目录内的 `.vscode` 配置。
4. 在新终端运行 `where.exe xelatex` 和 `where.exe latexmk`，确认程序在 PATH 中。编译配置不依赖某一台电脑的 TeX Live 安装位置。
5. 原始照片另由百度网盘下载。默认目录是 `NotePhotos/BaiduSyncdisk/`；若新设备使用其他路径，向 AI 提供实际位置。照片不需要下载到源码仓库中才能编译现有正文。
6. 继续转写前阅读相应科目的 `progress.md` 和转写指南，并验证照片已下载且实际可读。

项目 `.vscode` 随 Git 同步；VS Code Settings Sync 负责用户设置及所选扩展，两者各自独立。

## 编译与预览

在 VS Code 打开某科目的 `main.tex`，按 `Ctrl+Alt+B` 编译，按 `Ctrl+Alt+V` 预览。保存时也会触发编译。

也可以在对应科目目录运行：

```powershell
latexmk -xelatex -synctex=1 -interaction=nonstopmode -halt-on-error -file-line-error -outdir=build main.tex
```

PDF 位于各科目的 `build/main.pdf`。编译成功不表示数学内容或逐图转写已经验收。

需要同步最新 PDF 时，在仓库根目录执行以下命令（先成功编译相应科目）：

```powershell
Copy-Item -LiteralPath TexNote/algebra/build/main.pdf -Destination pdf/algebra.pdf
Copy-Item -LiteralPath TexNote/real_analysis/build/main.pdf -Destination pdf/real_analysis.pdf
```

只在整理完成、需要保存阅读版本时更新 `pdf/`，不必每次自动编译都提交 PDF。

## 日常同步

开始整理前先 `git pull`。完成并检查后执行：

```powershell
git add .
git diff --cached --stat
git commit -m "Update math notes"
git push
```

提交前确认文件列表中没有原始照片、编译产物或本地备份。同一批笔记尽量在一台设备整理并推送后，再换设备拉取继续。
