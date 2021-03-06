# 大连理工大学博士学位论文模版

## Tasks

### DONE

- 字体配置
- 页面设置
- 页面样式，例如，页眉、页脚等
- 论文封面与独创性声明
- 章节标题
- 目录，中英文章节目录、图目录和表目录
- 浮动体设置
- 插图设置

### DOING

- 参考文献

### TODO

- 交叉引用
- 文档链接
- 中英文摘要
- 数学公式排版

## 安装

## 使用说明

### 字体设置

### 页面设置

### 页眉页脚配置

### 封面

- [ ] 如何定义封面元素


### 章节标题

### 目录

#### 中文目录

中文目录

#### 英文目录

英文目录

### 浮动对象及其标题

### 图表

#### pgf/tikz

本模板默认载入`pgf`系列宏包（其中包括`pgf`、`tikz`、`pgfplots`与`pgfplotstable`四个宏包）。这些宏包提供了丰富的图形命令以满足论文写作中的作图需求。由于博士论文中往往插图较多，若这些插图又多以`pgf/tikz`宏包来完成，那么如果不进行特殊的处理的话，则在写作进行当中，每次编译都会将大量的时间消耗在绘图过程中。为了减少由此带来的影响，本模板提供了图形的预绘制接口，从而加快写作中的编译过程。这部分接口基于`pgf`中的`external`库，详细使用方法以及在本模板中的调用方式请参考

- [pgf文档](http://mirrors.ctan.org/graphics/pgf/base/doc/pgfmanual.pdf)
中Externalization Graphics一章，
- 文档类定义文件[dlutthesis.cls](https://github.com/Khaos/DLUTThesis/blob/master/dlutthesis.cls)中相关代码。

对于一般用户，可以忽略具体的实现细节，直接使用预绘制接口，方法如下：

1. 在主文档preamble部分指定主文档名称，例如

    ```latex
    \dlutset{pgf/externalmainfile=DLUTThesis}
    ```

1. 在正文需要插入tikz图形的位置，以如下格式插入图形

    ```latex
    \begin{figure}[!htbp]
    	\centering
    	\dlutset{pgf/makenextfig=pdf-filename}
    	\input{tikz-filename.tikz}
    	\caption{...}
    	\label{fig:id}
    \end{figure}%
    ```

1. 编译主文档

    ```shell
    xelatex -shell-escape DLUTThesis.tex
    ```

    默认采用增量编译的预绘制模式，即每次只重新绘制改动过的tikz图形。

1. （可选）进阶使用

    用户还可手动修改预绘制模式，例如在preamble如下设置后，

    ```latex
    \dlutset{
    	pgf/externalmode=list and make
    }
    ```

    就支持先单独编译每个tikz图形（以下 `pdf-filename` 代表插入tikz图形时设置的pdf文件名），再编译主文档。

    ```shell
    xelatex -shell-escape -halt-on-error -interaction=batchmode -jobname "pdf-filename" "DLUTThesis"
    ```

    选项 `pgf/externalmode` 是pgf选项 `/tikz/external/mode` 的别名，完整用法可查询pgf文档。

### 参考文献及其引用

本论文模板默认使用宏包`biblatex`以及相应的后端程序`biber`来进行参考文献的管理。大连理工大学参考文献格式符合《文后参考文献著录规则中华人民共和国国家标准 GB/T 7714—2005》，为满足这个要求，模板定义了符合该国家标准的`bst`文件来输出正确的参考文献格式。使用时请将相应的`bst`文件包含进你的文档目录中。

#### `biblatex`宏包


#### `biber`


#### 文献引用命令



## 参考文献

- [大连理工大学研究生院 -- 论文模版](http://gs.dlut.edu.cn/info/1099/7743.htm)
- [dlutlatextemplate](http://code.google.com/p/dlutlatextemplate/)  根据大连理工大学研究生院提供的Word学位论文模版制作的LaTeX模版


## LICENSE

Copyright [2016] [Dazhi Jiang]

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
