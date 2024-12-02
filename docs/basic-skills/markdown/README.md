# Markdown教程
[点我查看脚注](#注释)  
**目录**：  

- [Markdown教程](#markdown教程)
  - [1 入门基础](#1-入门基础)
    - [1.1 Markdown是什么](#11-markdown是什么)
    - [1.2 为什么要使用 Markdown？](#12-为什么要使用-markdown)
    - [1.3 Markdown 的工作原理](#13-markdown-的工作原理)
    - [1.4 Markdown有什么用？](#14-markdown有什么用)
    - [1.5 推荐工具](#15-推荐工具)
  - [2 环境配置](#2-环境配置)
  - [3 基础语法](#3-基础语法)
    - [3.1 换行](#31-换行)
    - [3.2 加粗倾斜](#32-加粗倾斜)
    - [3.3 线段](#33-线段)
      - [3.3.1 删除线（中划线）](#331-删除线中划线)
      - [3.3.2 分割线](#332-分割线)
    - [3.4 标题](#34-标题)
    - [3.5 列表](#35-列表)
      - [3.5.1 无序列表](#351-无序列表)
      - [3.5.2 有序列表](#352-有序列表)
      - [3.5.3 列表嵌套](#353-列表嵌套)
      - [3.5.4 勾选框](#354-勾选框)
    - [3.6 代码块](#36-代码块)
      - [3.6.1 代码块](#361-代码块)
      - [3.6.2 转义反引号](#362-转义反引号)
    - [3.7 引用](#37-引用)
    - [3.8 超链接](#38-超链接)
      - [3.8.1 链接and脚注](#381-链接and脚注)
      - [3.8.2 图片的插入](#382-图片的插入)
    - [3.9 表格](#39-表格)
  - [4 扩展语法](#4-扩展语法)
    - [4.1 高亮](#41-高亮)
    - [4.2 上标](#42-上标)
    - [4.3 下标](#43-下标)
    - [4.4 数学公式](#44-数学公式)
      - [4.4.1 单行](#441-单行)
      - [4.4.2 多行](#442-多行)
      - [4.4.3 数学符号](#443-数学符号)
  - [5 速查表](#5-速查表)


## 1 入门基础

### 1.1 Markdown是什么

Markdown 是一种轻量级的标记语言，可用于在纯文本文档中添加格式化元素。由 John Gruber 于 2004 年创建，如今已成为世界上最受欢迎的标记语言之一。

1. 专注于文字内容；
2. 纯文本，易读易写，可以方便地纳入版本控制；
3. 语法简单，没有什么学习成本，能轻松在码字的同时做出美观大方的排版。

>Markdown 语法的首要设计目标是尽可能易读。基于这个目标，Markdown 格式的文档能够以纯文本形式原样发布，而不会看起来像被填满了标签或格式化指令。

### 1.2 为什么要使用 Markdown？

* Markdown 无处不在。StackOverflow、CSDN、掘金、简书、GitBook、有道云笔记、V2EX、光谷社区等。主流的代码托管平台，如 GitHub、GitLab、BitBucket、Coding、Gitee 等等，都支持 Markdown 语法，很多开源项目的 README、开发文档、帮助文档、Wiki 等都用 Markdown 写作。

* Markdown 是纯文本可移植的。几乎可以使用任何应用程序打开包含 Markdown 格式的文本文件。如果你不喜欢当前使用的 Markdown 应用程序了，则可以将 Markdown 文件导入另一个 Markdown 应用程序中。这与 Microsoft Word 等文字处理应用程序形成了鲜明的对比，Microsoft Word 将你的内容锁定在专有文件格式中。

* Markdown 是独立于平台的。你可以在运行任何操作系统的任何设备上创建 Markdown 格式的文本。

* Markdown 能适应未来的变化。即使你正在使用的应用程序将来会在某个时候不能使用了，你仍然可以使用文本编辑器读取 Markdown 格式的文本。当涉及需要无限期保存的书籍、大学论文和其他里程碑式的文件时，这是一个重要的考虑因素。

### 1.3 Markdown 的工作原理

Markdown 应用程序使用一种称为 Markdown 处理器（也通常称为“解析器”或“实现”）的东西将获取到的 Markdown 格式的文本输出为 HTML 格式。以便可以在 Web 浏览器中显示。  
由于各平台可能采用不同语言实现的 Markdown 解析引擎，或采用同一解析引擎的不同版本，而且可能有不同程度的定制与扩展，这导致在不同平台上使用 Markdown 写作时体验并不完全一致。不过对于大家公认的一些标准语法，各家还是支持的。

### 1.4 Markdown有什么用？

Markdown 是做笔记、为网站创建内容以及生成可打印文档的快速、简便的方法。
下面是一些你可以使用 Markdown 的场景
1. 网站
2. 文件资料
3. 笔记
4. 书籍
5. 演示文稿
6. 邮件
7. 文档

### 1.5 推荐工具

使用 Markdown 的过程中，最令人困惑的地方是：实际上每个 Markdown 应用程序都实现了稍有不同的 Markdown 语法。Markdown 的这些变体通常被称为 flavors（方言）。  
为了保持 Markdown 文件的可移植性，需要在其它应用程序中保存或使用 Markdown 文件。要实现这一点需要选择一个具有良好 Markdown 支持的应用程序。   
可以尝试以下工具  
1. [vscode](https://code.visualstudio.com/)  
2. [MarkdownPad](http://markdownpad.com/)  
3. [TEXTS](http://www.texts.io/)  
4. [在线工具](https://markdown.com.cn/editor/)  
5. [Markdown Tutorial](https://www.markdowntutorial.com/).开源网站,能用浏览器在这个网站上尝试 Markdown。  
6. [Awesome Markdown](https://github.com/mundimark/awesome-markdown).Markdown 工具和学习资源列表

## 2 环境配置

以下以vscode为例[官网地址](https://code.visualstudio.com/)

1. **安装vscode**


![点击进入下载界面](https://files.mdnice.com/user/75397/9fe73c81-77a6-4fb6-8266-64777c6a7d1d.jpg)


![根据自己的系统下载相关的即可，我这里是windos系统所以选择这个](https://files.mdnice.com/user/75397/80d61694-4187-4f73-8b60-462dcbeef7bd.jpg)


2. **下载完成点击运行，然后我们开始安装**


![](https://files.mdnice.com/user/75397/dff0f2cb-aa74-4ed8-a2d3-3817ad784c45.jpg)


3. **选择安装的位置**


![](https://files.mdnice.com/user/75397/91a0cf23-7207-4f10-b437-c79eed76aa6f.jpg)

4. **选择开始菜单文件夹**


![](https://files.mdnice.com/user/75397/540569a6-eba2-4d74-92e9-01862ee48264.jpg)

5. **选择附加任务**


![](https://files.mdnice.com/user/75397/92c981f9-4221-4b6d-9d20-204ad8a7a9e5.jpg)

6. **准备安装**


![](https://files.mdnice.com/user/75397/a314053f-69b8-4d7a-b2a6-958c19436064.jpg)

7. **结束并运行**


![](https://files.mdnice.com/user/75397/dd17f01f-807f-461e-822d-e0e4aa919dd0.jpg)

8. **汉化**


![](https://files.mdnice.com/user/75397/a0434c4b-5631-4efa-afa7-82fe12c7a6ac.jpg)

9. 安装Markdown扩展(根据需求安装)


  1. ![编辑Markdown必备扩展](https://files.mdnice.com/user/75397/ca9dba55-11b6-4767-8fc4-49728ebcf1f6.png)

  2. ![拥有快捷键、目录快速生成、自动预览等功能](https://files.mdnice.com/user/75397/3255ab0a-fa9d-4273-8470-c266969d109b.jpg)

        * 快捷键：例如，按Ctrl+B可以选择中的文本加粗
        * 目录生成：在文档中输入`[toc]`并保持，可以自动生成目录。

   3. ![预览增强插件](https://files.mdnice.com/user/75397/c868580d-2f7a-4810-be66-acc9b03f5bba.jpg)

        * 快捷键 Ctrl+Shift+V 可快速打开预览。
        * 快捷键 Ctrl+K V 可在侧边打开预览。
        * 自动同步：使用自动滚动同步功能，确保编辑和预览窗口内容同步。
        * 代码块执行：在 Markdown 中嵌入代码块，并使用 shift-enter 快捷键执行代码。


   4.  ![可以将 Markdown 文件转换为 PDF、HTML、PNG 或 JPEG 文件。](https://files.mdnice.com/user/75397/86d15796-e922-429f-8b87-ade4ed212f6b.jpg)

          * 按 F1 或 Ctrl+Shift+P，输入 markdown-pdf: Export，选择你需要的导出格式（如 PDF、HTML、PNG、JPEG）。
          * 自定义样式：通过 markdown-pdf.styles 配置自定义 CSS 文件，调整输出文件的样式。
          * 自动转换：启用 markdown-pdf.convertOnSave 功能，每次保存 Markdown 文件时自动生成 PDF。

  5. ![帮助开发者避免常见的 Markdown 错误和不良格式](https://files.mdnice.com/user/75397/0bb42576-8b96-402b-aa45-6d6d8d1cd9da.jpg)
        * 任何违反 markdownlint 规则的行都会在编辑器中触发警告。
        * 警告会以波浪线绿色下划线显示，也可以通过按 Ctrl+Shift+M 或 ⇧⌘M 打开错误和警告对话框查看。
        * 将鼠标悬停在绿色下划线上可以看到警告信息，或者按 F8 和 Shift+F8 循环查看所有警告。
        * 配置文件：使用 .markdownlint.json 文件来定制规则，以适应团队的具体需求
        * 自动修复：使用 markdownlint fixAll 命令自动修复文档中的常见问题。
        * 持续集成：将 markdownlint 集成到 CI 流程中，确保每次提交都经过格式检查。

   6. ![预览功能与GitHub的显示风格保持一致](https://files.mdnice.com/user/75397/2444744a-fe98-45bb-8317-4bc5c2f2822a.jpg)

        * Markdown Emoji - 增加表情符号支持.
        * Markdown Checkboxes - 支持任务列表。
        * Markdown YAML Preamble - 渲染YAML前缀为表格
        * Markdown Footnotes - 添加脚注支持
        * Markdown Mermaid - 支持Mermaid图表和流程图，丰富文档的表现形式

  7. ![](https://files.mdnice.com/user/75397/43b42d14-4793-47fa-aed1-2f789f9bc75e.jpg)

       * 自动预览Markdown

## 3 基础语法

注：换行、加粗倾斜、删除线、分割线、标题、列表(有序、无序)、超链接、图片、表格等都可以使用HTML。

### 3.1 换行

这是第一个段落的第一行文字[这是换行](在Markdown中如果想要换行，可以在这一行的最右端加入俩个空格以及一个回车；也可以用HTML "换行")——[点我看脚注[1]](#注释)    
这是第一个段落的第二行文字[这是换段落](在Markdown中如果想要换段落，可以在这一行的最右端加入俩个回车；也可以用HTML "换段")——[点我看脚注[2]](#注释) 

这是第二个段落的第一行文字。

### 3.2 加粗倾斜

|Markdown|HTML|效果|
|:---:|:---:|:---:|
|`**我是需要加粗的文字1**`|`<strong>我是需要加粗的文字1</strong>`|**我是需要加粗的文字1**|
|`需要一个空格 __我是需要加粗的文字2__ 需要一个空格`|`<b>我是需要加粗的文字2</b>`|需要一个空格 __我是需要加粗的文字2__ 需要一个空格|
|`*我是需要倾斜的文字1*`|`<em>我是需要倾斜的文字1</em>`|*我是需要倾斜的文字1*|
|`需要一个空格 _我是需要倾斜的文字2_ 需要一个空格`|`<i>我是需要倾斜的文字2</i>`|需要一个空格 _我是需要倾斜的文字2_ 需要一个空格|

|Markdown|HTML|效果|
|:---:|:---:|:---:|
|`***我是需要加粗倾斜的文字a***`|`<strong><em>我是需要加粗倾斜的文字a</em></strong>`|***我是需要加粗倾斜的文字a***|
|`需要一个空格 ___我是需要加粗倾斜的文字b___ 需要一个空格`|`<b><i>我是需要加粗倾斜的文字b</i></b>`|需要一个空格 ___我是需要加粗倾斜的文字b___ 需要一个空格|
|`需要一个空格 *__我是需要加粗倾斜的文字c__* 需要一个空格`|/|需要一个空格 *__我是需要加粗倾斜的文字c__* 需要一个空格|
|如果有下划线(`_`)表示加粗或倾斜，此时倘若俩边有字，需要用空格隔开|/|/|

### 3.3 线段
#### 3.3.1 删除线（中划线）

|Markdown|HTML|效果|
|:---:|:---:|:---:|
|`~~我是需要中划线的文字a~~`|`<del>我是需要加粗倾斜的文字a</del>`|~~我是需要中划线的文字a~~|
|`***~~我是需要加粗倾斜以及中划线的文字b~~***`|`<b><i><del>我是需要加粗倾斜以及中划线的文字b</del></i></b>`|***~~我是需要加粗倾斜以及中划线的文字b~~***|

#### 3.3.2 分割线

|Markdown|效果|
|:---:|:---:|
|[***](独占一行,三个`*`以上，可以有空格 "分割线的用法1")|[点我看脚注[3](#注释)|
|[- --](独占一行,三个`-`以上，`-`之间至少有一个空格 "分割线的用法2")|[点我看脚注[4]](#注释)|
|`***`|<hr></hr>|
|`- --`|<hr></hr>|

### 3.4 标题

|Markdown|效果|
|:---:|:---:|
|在Markdown里像这种单边的注释几乎都需要用空格隔开内容|/|
|`# 我是一级标题最大的标题`|<h1>我是一级标题最大的标题</h1>|
|`## 我是二级标题`|<h2>我是二级标题</h2>|
|`### 我是三级标题`|<h3>我是三级标题</h3>|
|`...`|`...`|
|###### 我是六级标题最小的标题|<h6>我是六级标题最小的标题</h6>|

[关于一级标题的其它用法](独占一行，一个`=`以上，`=`之间不可以有空格;对上一个段落的文本生效。 "一级标题的用法2")——[点我看脚注[5]](#注释)

[关于二级标题的其它用法](独占一行，一个`-`以上，`-`之间不可以有空格；对上一个段落的文本生效。 "二级标题的用法2")——[点我看脚注[6]](#注释)                                                  

### 3.5 列表

#### 3.5.1 无序列表

|Markdown|效果|
|:---:|:---:|
|`*`、`+`、`-`都可以做无序列表，当它们混着用的时候，各自代表不同的无序列表|/|
|`* 我是第一个无序列表的第一个任务`|<ul><li>我是第一个无序列表的第一个任务</li></ul>|
|`* 我是第一个无序列表的第二个任务`|<ul><li>我是第一个无序列表的第二个任务</li></ul>|
|`+ 我是第二个无序列表的第一个任务`|<ul><li>我是第二个无序列表的第一个任务</li></ul>|
|`+ 我是第二个无序列表的第二个任务`|<ul><li>我是第二个无序列表的第二个任务</li></ul>|
|`- 我是第三个无序列表的第一个任务`|<ul><li>我是第三个无序列表的第一个任务</li></ul>|
|`- 我是第三个无序列表的第二个任务`|<ul><li>我是第三个无序列表的第二个任务</li></ul>|
|`+ 我是第四个无序列表的第一个任务`|<ul><li>我是第四个无序列表的第一个任务</li></ul>|
|`- 我是第五个无序列表的第一个任务`|<ul><li>我是第五个无序列表的第一个任务</li></ul>|
|`* 我是第六个无序列表的第一个任务`|<ul><li>我是第六个无序列表的第一个任务</li></ul>|

#### 3.5.2 有序列表

|Markdown|效果|
|:---:|:---:|
|有序列表，除了第一项可以自定义数字大小(`非负整数`)，之后只能按照顺序排列|/|
|`1. 我是有序列表的第一个任务`|<ol><li>我是有序列表的第一个任务</li></ol>|
|`2. 我是有序列表的第二个任务`|<ol><li>...</li><li>我是有序列表的第二个任务</li></ol>|
|...|...|

#### 3.5.3 列表嵌套

一个`tab`嵌套一层：

```markdown
1. 我是第一项任务
    * 我是第一项任务的子任务
2. 我是第二项任务
    1. 我是第二项任务的任务1
        1. 我是第二项任务的任务1的任务1
    2. 我是第二项任务的任务2
3. 我是第三项任务
```

#### 3.5.4 勾选框

|Markdown|效果|
|:---:|:---:|
|`x`、`X`皆可；无论是用有序列表还是无序列表做勾选框，效果都是一样的，不显示序列号|/|
|`* [x] 主板`|* [x] 主板|
|`* [ ] 显卡`|* [ ] 显卡|
|`3. [ ] CPU`|3. [ ] CPU|

### 3.6 代码块

#### 3.6.1 代码块


[代码块的用法1](给代码缩进`4个空格`或者一个`tab`即可形成代码块 "代码块的用法1")——[点我看脚注[7]](#注释)

<table>
    <tr>
        <th>markdown</th>
        <th>效果解析</th>
    </tr>
    <tr>
        <td>
            ```语言<br>
            代码<br>
            ```
        </td>
        <td>
            与代码相对应的【语言】可以给予高亮
        </td>
    </tr>
</table>

#### 3.6.2 转义反引号

|Markdown|效果|
|:---:|:---:|
|\`代码`|`代码`|

### 3.7 引用

```markdown
> 在Markdown里它可以将之后文本引用。如果不想被引用需要 用`段落换行`

> ```markdown
> 可嵌套代码块
> ```

* 可被列表嵌套以及加粗倾斜
    * > ***sss***

> 第一层
>> 第二层
>>> 第三层
```

### 3.8 超链接

#### 3.8.1 链接and脚注

|Markdown|效果|
|:---:|:---:|
|`https://markdown.com.cn/editor/`|https://markdown.com.cn/editor/|
|`[官网](https://markdown.com.cn/editor/)`|[官网](https://markdown.com.cn/editor/)|
|`[官网][c]`<br>`[a][c]`<p></p>`[c]: https://markdown.com.cn/editor/`|[官网](https://markdown.com.cn/editor/)<br>[a](https://markdown.com.cn/editor/)|
|`[脚注](对a的解释说明 "a")`|[脚注[8]](对a的解释说明 "我是超链接中脚注a")|

#### 3.8.2 图片的插入

|Markdown|效果|
|:---:|:---:|
|`![](imgs/1.jpg)`|
![](https://files.mdnice.com/user/75397/b263da8b-d2c7-4fd3-893e-236f49eeea02.jpg)
|
|`[emm][1]`<br>`[wmm][1]`<p></p>`[1]: imgs/2.jpg`|
![](https://files.mdnice.com/user/75397/849fab74-effc-4218-8412-d99dfffbd475.jpg)
|

### 3.9 表格

<table>
    <tr>
        <th>
        markdown
        </th>
        <th>
        效果
        </th>
    </tr>
     <tr>
        <td>
        |姓名|年龄|性别|<br>
        |:---|---:|:---:|<br>
        |小明|14|男|
        </td>
        <td>
        <table>
            <tr>
                <th style="text-align:left">
                姓名
                </th>
                <th style="text-align:right">
                年龄
                </th>
                <th style="text-align:center">
                性别
                </th>
            </tr>
             <tr>
                <td style="text-align:left">
                小明
                </td>
                <td style="text-align:right">
                14
                </td>
                <td style="text-align:center">
                男
                </td>
            </tr>
        </table>
        </td>
    </tr>
</table>

## 4 扩展语法

注：扩展语法默认不支持 需要自己勾选(idea)

### 4.1 高亮

|Markdown|效果|
|:---:|:---:|
|`==高亮==`|<mark>高亮</mark>|

### 4.2 上标

|Markdown|效果|
|:---:|:---:|
|`x^2^2`|x²|

### 4.3 下标

|Markdown|效果|
|:---:|:---:|
|`x~2`|x₂|

### 4.4 数学公式

#### 4.4.1 单行

|Markdown|效果|
|:---:|:---:|
|`$x=1+y$`|$x=1+y$|

#### 4.4.2 多行

|Markdown|效果|
|:---:|:---:|
|`$$`<br>`x=1+y`<br>`$$`|$$x=1+y$$|

#### 4.4.3 数学符号

|Markdown|效果|效果|
|:---:|:---:|:---:|
|`$$`<br>`\\`<br>$$`|/|`\\换行`|
|`$$`<br>`\frac{x+1}{(y+2)(x+1)}`<br>`$$`|$$\frac{x+1}{(y+2)(x+1)}$$|\frac:分数|
|`$$`<br>`x^2`<br>`$$`|$$x^2$$|^:上标|
|`$$`<br>`x_2`<br>`$$`|$$x_2$$|_:下标|
|`$$`<br>`x_{it}^2x`<br>`$$`|$$x_{it}^2x$$|上下标|
|`$$`<br>`\sqrt[3]{\{[(43+x)+xy]\}}`<br>`$$`|$$\sqrt[3]{\{[(43+x)+xy]\}}$$|\sqrt[n]:$\sqrt[n]{x}$|
|`$$`<br>`x\not=2`<br>`$$`|$$x\not=2$$|\not=:$\not=$|
|`$$`<br>`x\approx2`<br>`$$`|$$x\approx2$$|\approx:$\approx$|
|`$$`<br>`x\leq2`<br>`$$`|$$x\leq2$$|\leq:$\leq$|
|`$$`<br>`x\geq2`<br>`$$`|$$x\geq2$$|\geq:$\geq$|
|`$$`<br>`x\times2=2x`<br>`$$`|$$x\times2=2x$$|\times:$\times$|
|`$$`<br>`x\div2=\frac{x}{2}`<br>`$$`|$$x\div2=\frac{x}{2}$$|\div:$\div$|
|`$$`<br>`\pm\sqrt{3}`<br>`$$`|$$\pm\sqrt{3}$$|\pm:$\pm$|
|`$$`<br>`\sum^2_2`<br>`$$`|$$\sum^2_2$$|求和符号<br>\sum:$\sum$|
|`$$`<br>`\prod^2_2`<br>`$$`|$$\prod^2_2$$|累乘符号<br>\prod:$\prod$|
|`$$`<br>`\coprod^2_2`<br>`$$`|$$\coprod^2_2$$|累除符号<br>\coprod:$\coprod$|
|`$$`<br>`\overline{1+2+3=4}`<br>`$$`|$$\overline{1+2+3=4}$$|求平均值符号<br>\overline:$\overline{1+2+3}$|
|`$$`<br>`90^\circ`<br>`$$`|$$90^\circ$$|多少度<br>\circ:$\circ$|
|`$$`<br>`\pi`<br>`$$`|$$\pi$$|圆周率<br>\pi:$\pi$|
|`$$`<br>`\infty`<br>`$$`|$$\infty$$|无穷<br>\infty:$\infty$|
|`$$`<br>`\iint_0^1x^2dx`<br>`$$`|$$\iint_0^1x^2dx$$|定积分<br>\int:$\int$|
|`$$`<br>`y\prime`<br>`$$`|$$y\prime$$|求导<br>\prime:$\prime$|
|`$$`<br>`\lim_{n\rightarrow+\infty}\frac{1}{n}`<br>`$$`|$$\lim_{n\rightarrow+\infty}\frac{1}{n}$$|求极限<br>\lim:$\lim$|
|`$$`<br>`\emptyset`<br>`$$`|$$\emptyset$$|空集<br>\emptyset:$\emptyset$|
|`$$`<br>`\in`<br>`$$`|$$\in$$|属于<br>\in:$\in$|
|`$$`<br>`\notin`<br>`$$`|$$\notin$$|不属于<br>\notin:$\notin$|
|`$$`<br>`\supset`<br>`$$`|$$\supset$$|真包含<br>\supset:$\supset$|
|`$$`<br>`\supseteq`<br>`$$`|$$\supseteq$$|包含<br>\supseteq:$\supseteq$|
|`$$`<br>`\bigcap`<br>`$$`|$$\bigcap$$|交集<br>\bigcap:$\bigcap$|
|`$$`<br>`\bigcup`<br>`$$`|$$\bigcup$$|并集<br>\bigcup:$\bigcup$|
|`$$`<br>`\alpha`<br>`$$`|$$\alpha$$|<br>\alpha:$\alpha$|
|`$$`<br>`\beta`<br>`$$`|$$\beta$$|<br>\beta:$\beta$|
|`$$`<br>`\gamma`<br>`$$`|$$\gamma$$|<br>\gammao:$\gamma$|
|`$$`<br>`\delta`<br>`$$`|$$\delta$$|<br>\delta:$\delta$|
|`$$`<br>`\eta`<br>`$$`|$$\eta$$|<br>\eta:$\eta$|
|`$$`<br>`\omega`<br>`$$`|$$\omega$$|<br>\omega:$\omega$|
|`$$`<br>`\theta`<br>`$$`|$$\theta$$|<br>\theta:$\theta$|
|`$$`<br>`\sigma`<br>`$$`|$$\sigma$$|<br>\sigma:$\sigma$|
|`$$`<br>`\mu`<br>`$$`|$$\mu$$|<br>\mu:$\mu$|
|`$$`<br>`\epsilon`<br>`$$`|$$\epsilon$$|<br>\epsilon:$\epsilon$|
|`$$`<br>`\cdots`<br>`$$`|$$\cdots$$|<br>\cdots:$\cdots$|
|`$$`<br>`\cdot`<br>`$$`|$$\cdot$$|<br>\cdot:$\cdot$|
|`$$`<br>`\ldots`<br>`$$`|$$\ldots$$|<br>\ldots:$\ldots$| 

## 5 [速查表](https://www.cnblogs.com/mengsuenyan/p/12614058.html#toc)

<a id="注释"></a>