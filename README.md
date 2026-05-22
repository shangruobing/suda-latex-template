# 苏州大学硕士学位论文模板

## 特性

- 更新至2026年6月，遵循苏大研究生学位论文最新要求
- Overleaf, TeXPage, TeXLive 和 MacTex 均编译正常
- 内置字体文件
- 详细的注释，若后续学校变更排版要求，方便自行修改

## 快速开始

1. 克隆或下载本仓库
2. 编辑 `content/0_0_info.tex` 填写论文基本信息
3. 使用VSCode或终端编译（见下文详细说明）

### 目录介绍

```text
├── content/                  # 论文内容
│   ├── 0_0_info.tex          # 论文元信息（必填）
│   ├── 0_1_abstract-zh.tex   # 中文摘要
│   ├── 1_introduction.tex    # 引言
│   └── ...
├── fonts/                    # 字体文件
├── img/                      # 图片资源（校徽等）
├── doc/                      # 额外的 docx 文件
├── pdf/                      # 额外的 pdf 文件
├── main.tex                  # 主文档
├── reference.bib             # 参考文献
├── sudathesis.bst            # 参考文献样式文件
├── sudathesis.cls            # 模板类文件
└── ...
```

### 推荐环境

- 安装 `TeX` 发行版，`TexLive` 或 `MacTex`
- 使用 `Visual Studio Code` 编辑器进行编辑，并安装 `LaTeX Workshop` 插件

#### 相关下载链接

- [TeXLive官网](https://tug.org/texlive/)
- [TeXLive清华镜像](https://mirrors.tuna.tsinghua.edu.cn/CTAN/systems/texlive/Images/)
- [Visual Studio Code官网](https://code.visualstudio.com/)

### 使用VSCode进行编译（推荐）

首先配置 `LaTeX Workshop` 插件：

1. 在 `VSCode` 中，打开设置（`Ctrl + ,`）
2. 搜索 `latex-workshop.latex.recipes`
3. 点击 `在 settings.json 中编辑`，添加如下内容：

```json
{
  "latex-workshop.latex.recipes": [
    {
      "name": "xe->bibtex->xe*2",
      "tools": ["xelatex", "bibtex", "xelatex", "xelatex"]
    }
  ]
}
```

插件配置完成后，按以下步骤编译并生成PDF：

1.  点击侧边栏的 `TEX` 图标
2.  选择 `COMMANDS`
3.  点击 `Build LaTeX project`
4.  在弹出菜单中，选择编译方案：`Recipe: xe->bibtex->xe*2`

### 使用终端进行编译

**使用 xelatex 进行编译，命令如下：**

```shell
xelatex main.tex
bibtex main
xelatex main.tex
xelatex main.tex
```

**清理编译结果文件，命令如下：**

```shell
make clear
```

## 参考

### 官方资料

苏州大学研究生学位论文基本格式.doc

> 来源：https://library.suda.edu.cn/4141/listm.htm

### 仓库

- https://github.com/huhamhire/sudathesis

- https://github.com/tianhaoo/Soochow-University-Thesis-Overleaf-LaTeX-Template

- https://github.com/shadowofgost/sudathesis-soochow-university-latex-template
- https://github.com/fairyshine/SUDA_TeX_Template

## 反馈

如果您发现任何问题或有改进建议，请在GitHub仓库提交Issue。

## 常见问题

### 关于封面、送审封面等页面的使用

**问题**：在使用模板时，封面格式与学校要求不符。

**解决方法**：

1. 使用学校提供的 Word 模板生成封面、送审封面等页面，并将生成的 PDF 文件放入 `pdf/` 目录。
2. 在 `main.tex` 中使用 `\includepdf` 命令引入这些 PDF 文件，例如：

```latex
\includepdf[pages=-]{pdf/封面.pdf}
```

---

### 参考文献显示异常或不显示

**问题**：在 VSCode 中使用 LaTeX Workshop 的 `Recipe: xe->bibtex->xe*2` 编译后，参考文献显示异常或不显示。

**原因**：项目文件中存在魔法注释，例如：

```latex
% !TEX program=xelatex
```

该注释会覆盖编译配方，使插件跳过 `bibtex` 步骤，导致参考文献无法正确生成。

**解决方法**：

1. **删除项目中的魔法注释**：

```latex
% !TEX program=xelatex
```

2. **在插件中设置禁用魔法注释**：
   - 打开 VSCode 设置
   - 搜索 `latex-workshop.latex.build.enableMagicComments`
   - 将其设置为 `false`

完成后重新使用 `Recipe: xe->bibtex->xe*2` 编译，即可正确生成参考文献。

---
