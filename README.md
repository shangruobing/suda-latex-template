# 苏州大学硕士学位论文模板

## 目录介绍

- content/ 文件夹内编写论文主要内容
  - 0_0_info.tex 论文元信息，如作者姓名、所属机构等
- fonts/ 编译 PDF 所需的字体文件
- img/ 必要的图片，如校徽等
- pdf/ 额外的 pdf 文件，在 main.tex 中导入
- reference.bib 参考文献

## 使用

**使用 xelatex 进行编译，命令如下：**

```shell
xelatex main.tex
bibtex main
xelatex main.tex
xelatex main.tex
```

**清理编译结果文件，命令如下：**

````shell
make clear
````

## 特性

- Overleaf, TexPage 和 MacTex(TexLive 的 mac 版本)均编译正常
- 完全遵循苏大研究生学位论文基本格式
- 内置字体文件
- 详细的注释，若后续学校变更排版要求，方便自行修改。

## 参考

### 官方资料

苏州大学研究生学位论文基本格式.doc

> 来源：https://library.suda.edu.cn/4141/listm.htm

### 仓库

https://github.com/huhamhire/sudathesis

https://github.com/tianhaoo/Soochow-University-Thesis-Overleaf-LaTeX-Template

https://github.com/shadowofgost/sudathesis-soochow-university-latex-template
