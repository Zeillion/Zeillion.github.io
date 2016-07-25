---
title: markdwoownSyntax
date: 2016-07-25 16:02:15
tags: [markdown]
---

#特殊字符自动转换
在 HTML 文件中，有两个字符需要特殊处理： < 和 & 。 < 符号用于起始标签，& 符号则用于标记 HTML 实体，如果你只是想要显示这些字符的原型，你必须要使用实体的形式，像是 &lt; 和 &amp;。

& 字符尤其让网络文档编写者受折磨，如果你要打「AT&T」 ，你必须要写成`「AT&amp;T」`。而网址中的 & 字符也要转换。

 1. &copy; :`&copy;`
 2. AT&T 	:`&amp;`
 3. 4 < 5 : `5 &lt 4`

<!--more-->

#区块元素
##段落和换行
一个 Markdown 段落是由一个或多个连续的文本行组成，它的前后要有一个以上的空行（空行的定义是显示上看起来像是空的，便会被视为空行。比方说，若某一行只包含空格和制表符，则该行也会被视为空行）。普通段落不该用空格或制表符来缩进。

「由一个或多个连续的文本行组成」这句话其实暗示了 Markdown 允许段落内的强迫换行（插入换行符），这个特性和其他大部分的 text-to-HTML 格式不一样（包括 Movable Type 的「Convert Line Breaks」选项），其它的格式会把每个换行符都转成 `<br />` 标签。

如果你确实想要依赖 Markdown 来插入 `<br />` 标签的话，在插入处先按入两个以上的空格然后回车。

的确，需要多费点事（多加空格）来产生 `<br />` ，但是简单地「每个换行都转换为 `<br />」`的方法在 Markdown 中并不适合， Markdown 中 email 式的 区块引用 和多段落的 列表 在使用换行来排版的时候，不但更好用，还更方便阅读。

##标题
Markdown 支持两种标题的语法，类 Setext 和类 atx 形式。

类 Setext 形式是用底线的形式，利用 = （最高阶标题）和 - （第二阶标题），例如：

	This is an H1
	=============
	
	This is an H2
	-------------
任何数量的 = 和 - 都可以有效果。

类 Atx 形式则是在行首插入 1 到 6 个 # ，对应到标题 1 到 6 阶，例如：

	# 这是 H1
	
	## 这是 H2
	
	###### 这是 H6

你可以选择性地「闭合」类 atx 样式的标题，这纯粹只是美观用的，若是觉得这样看起来比较舒适，你就可以在行尾加上 #，而行尾的 # 数量也不用和开头一样（行首的井字符数量决定标题的阶数）：

	# 这是 H1 #
	
	## 这是 H2 ##
	
	### 这是 H3 ######

##区块引用Blockquotes
Markdown 标记区块引用是使用类似 email 中用 > 的引用方式。如果你还熟悉在 email 信件中的引言部分，你就知道怎么在 Markdown 文件中建立一个区块引用，那会看起来像是你自己先断好行，然后在每行的最前面加上 > ：
	
	> This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
	> consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
	> Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.
	> 
	> Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse
	> id sem consectetuer libero luctus adipiscing.

Markdown 也允许你偷懒只在整个段落的第一行最前面加上 > ：

	> This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
	consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
	Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.
	
	> Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse
	id sem consectetuer libero luctus adipiscing.
区块引用可以嵌套（例如：引用内的引用），只要根据层次加上不同数量的 > ：

	 This is the first level of quoting.
	>
	> > This is nested blockquote.
	>
	> Back to the first level.
引用的区块内也可以使用其他的 Markdown 语法，包括标题、列表、代码区块等：

	> ## 这是一个标题。
	> 
	> 1.   这是第一行列表项。
	> 2.   这是第二行列表项。
	> 
	> 给出一些例子代码：
	> 
	>     return shell_exec("echo $input | $markdown_script");
任何像样的文本编辑器都能轻松地建立 email 型的引用。例如在 BBEdit 中，你可以选取文字后然后从选单中选择增加引用阶层。

##列表
Markdown 支持有序列表和无序列表。

无序列表使用星号、加号或是减号作为列表标记：

	*   Red
	*   Green
	*   Blue
等同于：

	+   Red
	+   Green
	+   Blue
也等同于：

	-   Red
	-   Green
	-   Blue
有序列表则使用数字接着一个英文句点：

	1.  Bird
	2.  McHale
	3.  Parish

列表项目可以包含多个段落，每个项目下的段落都必须缩进 4 个空格或是 1 个制表符：

	1.  This is a list item with two paragraphs. Lorem ipsum dolor
	    sit amet, consectetuer adipiscing elit. Aliquam hendrerit
	    mi posuere lectus.
	
	    Vestibulum enim wisi, viverra nec, fringilla in, laoreet
	    vitae, risus. Donec sit amet nisl. Aliquam semper ipsum
	    sit amet velit.
	
	2.  Suspendisse id sem consectetuer libero luctus adipiscing.
如果你每行都有缩进，看起来会看好很多，当然，再次地，如果你很懒惰，Markdown 也允许：

	*   This is a list item with two paragraphs.
	
	    This is the second paragraph in the list item. You're
	only required to indent the first line. Lorem ipsum dolor
	sit amet, consectetuer adipiscing elit.
	
	*   Another item in the same list.
如果要在列表项目内放进引用，那 > 就需要缩进：

	*   A list item with a blockquote:
	
	    > This is a blockquote
	    > inside a list item.
如果要放代码区块的话，该区块就需要缩进两次，也就是 8 个空格或是 2 个制表符：

	*   一列表项包含一个列表区块：
	
	        <代码写在这>

##代码区块
要在 Markdown 中建立代码区块很简单，只要简单地缩进 4 个空格或是 1 个制表符就可以，例如，下面的输入：

	这是一个普通段落：
	
	    这是一个代码区块。
也可以使用如下方法指定语言：

	```python
		def aa():
			print 1
	```
或者如下：

	`
		code is here!
	`

###分隔线
你可以在一行中用三个以上的星号、减号、底线来建立一个分隔线，行内不能有其他东西。你也可以在星号或是减号中间插入空格。下面每种写法都可以建立分隔线：

	* * *
	
	***
	
	*****
	
	- - -
	
	---------------------------------------

#区段元素

##链接
Markdown 支持两种形式的链接语法： 行内式和参考式两种形式。

不管是哪一种，链接文字都是用 [方括号] 来标记。

要建立一个行内式的链接，只要在方块括号后面紧接着圆括号并插入网址链接即可，如果你还想要加上链接的 title 文字，只要在网址后面，用双引号把 title 文字包起来即可，例如：
	
	This is [an example](http://example.com/ "Title") inline link.
	
	[This link](http://example.net/) has no title attribute.

如果你是要链接到同样主机的资源，你可以使用相对路径：

	See my [About](/about/) page for details.
参考式的链接是在链接文字的括号后面再接上另一个方括号，而在第二个方括号里面要填入用以辨识链接的标记：

	This is [an example][id] reference-style link.
你也可以选择性地在两个方括号中间加上一个空格：

	This is [an example] [id] reference-style link.
接着，在文件的任意处，你可以把这个标记的链接内容定义出来：

	[id]: http://example.com/  "Optional Title Here"
链接内容定义的形式为：

* 方括号（前面可以选择性地加上至多三个空格来缩进），里面输入链接文字
* 接着一个冒号
* 接着一个以上的空格或制表符
* 接着链接的网址
* 选择性地接着 title 内容，可以用单引号、双引号或是括弧包着

下面这三种链接的定义都是相同：

	[foo]: http://example.com/  "Optional Title Here"
	[foo]: http://example.com/  'Optional Title Here'
	[foo]: http://example.com/  (Optional Title Here)

隐式链接标记功能让你可以省略指定链接标记，这种情形下，链接标记会视为等同于链接文字，要用隐式链接标记只要在链接文字后面加上一个空的方括号，如果你要让 "Google" 链接到 google.com，你可以简化成：

	[Google][]

链接的定义可以放在文件中的任何一个地方，我比较偏好直接放在链接出现段落的后面，你也可以把它放在文件最后面，就像是注解一样。

下面是一个参考式链接的范例：

	I get 10 times more traffic from [Google] [1] than from
	[Yahoo] [2] or [MSN] [3].
	
	  [1]: http://google.com/        "Google"
	  [2]: http://search.yahoo.com/  "Yahoo Search"
	  [3]: http://search.msn.com/    "MSN Search"

## 强调
Markdown 使用星号`（*）`和底线`（_）`作为标记强调字词的符号，被 `*` 或 `_ `包围的字词会被转成用 `<em> `标签包围，用两个 `* `或 `_` 包起来的话，则会被转成 <strong>，例如：

	*single asterisks*
	
	_single underscores_
	
	**double asterisks**
	
	__double underscores__


##图片

![image](markdwoownSyntax/1.jpg)

行内式的图片语法看起来像是：
```
	![Alt text](/path/to/img.jpg)
	![Alt text](/path/to/img.jpg "Optional title")
```


#其它
##反斜杠

Markdown 可以利用反斜杠来插入一些在语法中有其它意义的符号，例如：如果你想要用星号加在文字旁边的方式来做出强调效果（但不用 `<em>` 标签），你可以在星号的前面加上反斜杠：

`\*literal asterisks\*`

Markdown 支持以下这些符号前面加上反斜杠来帮助插入普通的符号：
	
	\   反斜线
	`   反引号
	*   星号
	_   底线
	{}  花括号
	[]  方括号
	()  括弧
	#   井字号
	+   加号
	-   减号
	.   英文句点
	!   惊叹号

##自动链接
	<http://example.com/>

Markdown 会转为：

	<a href="http://example.com/">http://example.com/</a>


#mark
抄自markdwon文档 <http://www.markdown.cn>


