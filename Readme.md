# 702学位论文Latex模板

本模板用于对学位论文进行格式排版。

文件夹中含有[Latex入门手册](manuals/Latex手册.pdf)。

---
**`format.sty`和`main.tex`文件的内容不要随意修改！！！**

---

## 目录

[TOC]

## 模板介绍

论文模板支持以下排版功能：

1. 硕/博士论文封面/扉页，博士英文扉页排版
2. 中英文摘要排版
3. 目次，图/表目录排版
4. 全文格式排版，包括章节标题、图表标题等
5. 图表公式排版，支持长表格
6. 支持阅读模式和打印模式两种输出模式



## 编辑/编译环境准备

### 本地环境

在线安装:

1. 安装`texlive`([安装教程](https://blog.csdn.net/Daniel_tanxz/article/details/134537213))，可以选择[官网](https://tug.org/texlive/)或者其他[镜像网站](https://mirrors.tuna.tsinghua.edu.cn/CTAN/systems/texlive/Images/)，镜像网站的下载速度更快
2. 安装编辑器，可以选择[texstudio](https://texstudio.sourceforge.net/)([安装教程](https://blog.csdn.net/Daniel_tanxz/article/details/134537213))或[VS Code](https://code.visualstudio.com/) + [Latex Workshop](https://github.com/James-Yu/LaTeX-Workshop.git)，两种方式都是免费的。。本人采用的是VS Code进行编辑，操作更方便，界面更美观

离线安装:

1. `texlive`与`texstudio`[离线安装教程](https://zhuanlan.zhihu.com/p/138586028)
2. `Latex Workshop`离线安装，在[插件市场](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)下载.visx插件文件([下载教程](https://zhuanlan.zhihu.com/p/32199377))，然后[离线安装](https://blog.csdn.net/r657225738/article/details/108460875)。

### 远程环境

[Overleaf](https://www.overleaf.com/)可以方便地实现在线latex文档编译，但由于学位论文篇幅一般较长，免费账户可能使用不便，不推荐。

## 模板结构

论文模板包含以下两个部分：

1. 内容模板
2. 格式模板

### 内容模板

内容模板根据学位论文的内容结构进行安排，包括以下部分：

1. 封面
2. 中文扉页/博士英文扉页
3. 学位论文原创性声明
4. 中/英文摘要
5. 目次
6. 图表目录
7. 正文
   1.  第1章 绪论
   2.  第x章 正文内容
   3.  第n章 总结与展望
8.  参考文献
9.  致谢
10. 学术论文和科研成果目录

### 格式模板

格式模板主要包括以下三个部分：

1. 图片模板
2. 表格模板
3. 公式模板
3. 引用与参考文献模板

## 模板使用方法

### 编译

本模板采用`ctex`中文支持包和`biblatex`引用文献包，需要采用如下编译顺序：
```
xelatex -> biber -> xelatex -> xelatex
```

编译教程:

1. [texstudio](https://blog.csdn.net/qq_15054345/article/details/127916752)
2. [vscode(Latex Workshop插件)](https://zhuanlan.zhihu.com/p/670991054)

### 内容模板使用

内容模板用于对论文内容格式进行排版，使用时需采取以下步骤：

1. 填写论文相关信息:
   
   在[myinfo.sty](template/myinfo.sty)文件中填写学位论文相关信息，编译即可自动排版内封面、页眉等论文相关信息

2. 撰写中英文摘要:
   
   在[chapters/abstract.sty](template/chapters/abstract.tex)文件中写入摘要和关键词

3. 撰写论文正文内容:
   
   在绪论、正文章节、总结与展望中撰写论文内容，建议各章分别写入不同文件并放置于[chapters](template/chapters)文件夹中，如[chapters/chapter-1.tex](template/chapters/chapter-1.tex)。
   
   在[chapters.tex](template/chapters.tex)文件内引用各章节，如`\include{chapters/chapter-1}`。
   
   章节结构为`\section`(章)，`\subsection`(节)，`\subsubsection`(小节)，参考[chapters/chapter-1.tex](template/chapters/chapter-1.tex)。
   
   图片、表格、公式及引用文献的输入参考**格式模板使用**。

4. 撰写致谢:
   
   在[chapters/acknowledgements.tex](template/chapters/acknowledgements.tex)文件中写入致谢

5. 编写学术论文和科研成果目录:
   
   在[chapters/achievements.tex](template/chapters/achievements.tex)文件中写入学术论文和科研成果目录

在部分或全部完成论文撰写后，进行编译即可生成符合模板的`.pdf`文件。

**重要提醒**：

1. `format.sty`和`main.tex`文件不要随意修改
2. 支持单双面打印排版，默认为双面打印排版，设置单面打印只需将[main.tex](template/main.tex)文件中首行的`twoside`改为`oneside`即可，即:
   
   ```latex
   \documentclass[twoside]{article} 
   % 改为:
   \documentclass[oneside]{article} 
   ```

3. 建议不要删除[chapters/abstract.sty](template/chapters/abstract.tex)(摘要)，[chapters/acknowledgements.tex](template/chapters/acknowledgements.tex)(致谢)和[chapters/achievements.tex](template/chapters/achievements.tex)(学术成果)这三个文件，直接对内容进行修改即可
4. 章节内容文件撰写完毕需要在[chapters.tex](template/chapters.tex)文件内引用，如`\include{chapters/chapter-1}`；如果需要每章首页都在奇数页上，只需在前方添加`\newoddpage`，如:
   
   ```latex
   \newoddpage % 创建新的奇数页
   \include{chapters/chapter-1}
   ```

### 格式模板使用

格式模板用于对图片、表格、引用和参考文献进行排版，使用方法如下：

#### 图片模板

图片源文件放于[figures](template/figures)文件夹中，插入图片时使用自定义环境`myfigure`可在当前文本位置插入**水平居中**图片：

```latex
\begin{myfigure}
   % 图片内容
   \includegraphics[width=0.6\textwidth]{figures/fig-1.png} % 图片宽度占页面宽度0.6
   \caption{} % 子图片题注，如 XXX示意图
   \caption{} % 题注内容，如 XXX示意图
   \label{} % 标签，如 fig:fig-1
\end{myfigure}
```

子图片可以在自定义环境`myfigure`内采用环境`subfigure`:

```latex
\begin{myfigure}
   % 子图片1
   \begin{subfigure}[b]{0.4\textwidth} % 子图片宽度占页面宽度0.4
      \centering % 子图片居中
      \includegraphics[width=\textwidth]{figures/subfig-1.png}
      \caption{} % 子图片题注，如 XXX示意图
      \label{} % 子图片标签，如 subfig:subfig-1		
   \end{subfigure}
   % 子图片2
   \begin{subfigure}[b]{0.6\textwidth} % 子图片宽度占页面宽度0.6
      \centering % 子图片居中
      \includegraphics[width=\textwidth]{figures/subfig-2.png}
      \caption{} % 子图片题注，如 XXX示意图
      \label{} % 子图片标签，如 subfig:subfig-1		
   \end{subfigure}
   \caption{} % 题注内容，如 XXX示意图
   \label{} % 标签，如 fig:fig-1
\end{myfigure}
```


引用图片的方法可以参考[Latex手册](manuals/Latex手册.pdf)，[chapters/chapter-1.tex](template/chapters/chapter-1.tex)中也给出了几个样例。

#### 表格模板

插入表格时使用自定义环境`mytable`可在当前文本位置插入**水平居中，五号字体**表格：

```latex
\begin{mytable}
   \caption{} % 题注内容，如 XXX参数表
   \label{} % 标签，如 tab:table-1
   % 表格内容
   ······
\end{mytable}
```

latex对于跨页长表格排版不太友好，如果需要跨页长表格可以使用自定义环境`mylongtable`: 

```latex
\begin{mylongtable} % mylongtable是自定义环境，题注和标签无需使用\caption{}和\label{}
   {} % 表格排版格式
   {} % 题注内容，如 XXX参数表
   {} % 标签，如 tab:longtable-1
   {} % 首页表头
   {} % 后续页表头
   {} % 除最后页以外的表尾
   {} % 最后页表尾
   % 表格内容
   ......
\end{mylongtable}
```

模板中[chapters/chapter-1.tex](template/chapters/chapter-1.tex)中也有跨页长表格样例，可以作为参考。

#### 公式模板

公式使用latex环境即可，如下：

```latex
\begin{equation}
  ······
\end{equation}
```

子公式可采用`subequations`环境配合`align`或`gather`环境，如下：
```latex
\begin{subequations}
	\begin{align} % align -> 子公式在符号 & 处对齐
	y5=&x5+z5+1 \\ % 编号为(1.1a)
	y6=&x6+z6+1+2 \notag \\ % \notag -> 不编号
	y7=&x7+z7 \label{eq:1b} % 编号为(1.1b)，可以通过\cref{eq:1b}引用子公式
	\end{align}
\end{subequations}
%
\begin{subequations}
	\begin{gather} % gather -> 子公式居中对齐
	y5=&x5+z5+1 \\ % 编号为(1.1a)
	y6=&x6+z6+1+2 \notag \\ % \notag -> 不编号
	y7=&x7+z7 \label{eq:1b} % 编号为(1.1b)，可以通过\cref{eq:1b}引用子公式
	\end{gather}
\end{subequations}
```

多行公式或更复杂的数学公式排版可参考[Latex手册](manuals/Latex手册.pdf)或[网络教程](https://www.overleaf.com/learn/latex/Learn_LaTeX_in_30_minutes)。

#### 引用与参考文献模板

参考文献需要以`bibtex`或`biblatex`引用格式存放于[references.bib](template/references.bib)文件中。

引用时使用`\cite{}`可进行上标引用，使用`\parencite{}`可进行水平引用，编译后文内自动生成参考文献列表。

#### 图片、表格、公式、章节的交叉引用

latex中交叉引用通过标签`\label{}`和引用`\cref{}`实现。

在图片、表格、公式、章节的定义处添加标签，如:
```latex
\label{fig:fig-1}
\label{tab:tab-1}
\label{eq:eq-1}
\label{sec:sec-1}
\label{ssec:subsec-1}
\label{sssec:subsubsec-1}
```

交叉引用只需在引用处添加`\cref{}`，如:
```latex
\cref{fig:fig-1} % 图1.1
\cref{tab:tab-1} % 表1.1
\cref{eq:eq-1} % 式(1.1)
\cref{sec:sec-1} % 第1章
\cref{ssec:subsec-1} % 1.1节
\cref{sssec:subsubsec-1} % 1.1.1小节
```

## 附录
`VS Code` + `Latex Workshop`配置文件:

```json
{  
    "latex-workshop.latex.recipes": [
        {
            "name": "pdflatex -> bibtex -> pdflatex * 2",
            "tools": [
                "pdflatex",
                "bibtex",
                "pdflatex",
                "pdflatex"
            ]
        },
        {
            "name": "xelatex -> biber -> xelatex * 2",
            "tools": [
                "xelatex",
                "biber",
                "xelatex",
                "xelatex"
            ]
        }
    ],
    "latex-workshop.latex.tools": [
        {
            "name": "pdflatex",
            "command": "pdflatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "-output-directory=output",
                "%DOC%"
            ]
        },
        {
            "name": "xelatex",
            "command": "xelatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "-pdf",
                "-xelatex",
                "-output-directory=output",
                "%DOC%"
            ]
        },
        {
            "name": "bibtex",
            "command": "bibtex",
            "args": [
                "output/%DOCFILE%"
            ]
        }
    ],
    "latex-workshop.latex.clean.fileTypes": [
        "%DOCFILE%.aux",
        "%DOCFILE%.bbl",
        "%DOCFILE%.blg",
        "%DOCFILE%.idx",
        "%DOCFILE%.ind",
        "%DOCFILE%.lof",
        "%DOCFILE%.lot",
        "%DOCFILE%.out",
        "%DOCFILE%.toc",
        "%DOCFILE%.acn",
        "%DOCFILE%.acr",
        "%DOCFILE%.alg",
        "%DOCFILE%.glg",
        "%DOCFILE%.glo",
        "%DOCFILE%.gls",
        "%DOCFILE%.fls",
        "%DOCFILE%.log",
        "%DOCFILE%.fdb_latexmk",
        "%DOCFILE%.snm",
        "%DOCFILE%.synctex(busy)",
        "%DOCFILE%.synctex.gz(busy)",
        "%DOCFILE%.nav",
        "%DOCFILE%.vrb"
    ],
    "latex-workshop.latex.autoBuild.run": "never",
    // 编译输出文件夹
    "latex-workshop.latex.outDir": "./output",
    // 设置为onFaild 在构建失败后清除辅助文件
    "latex-workshop.latex.autoClean.run": "onFailed",
    // 使用上次的recipe编译组合
    "latex-workshop.latex.recipe.default": "lastUsed",
}
```