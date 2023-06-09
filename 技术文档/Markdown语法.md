## Markdown语法

1. **段落和换行：**
一个 Markdown 段落是由一个或多个连续的文本行组成，它的前后要有一个以上的空行。
2. **标题**：用#标识符表示，从#--》######。例如：
3. **区块引用**：在段落的第一行最前面加">"
区块引用可以嵌套（例如：引用内的引用），只要根据层次加上不同数量的 > ：
区块内也可以套用其他的 Markdown 语法，包括加粗、列表、代码区块等：
4. **列表**
Markdown 支持有序列表和无序列表。
   * 无序列表，无序列表使用星号*、加号+或是减号- 作为列表标记，效果一样；
   + 有序列表，有序列表则使用数字接着一个英文句点。
5. **代码区块**
要在 Markdown 中建立代码区块很简单，只要简单地缩进 4 个空格或是 1 个制表符就可以，例如，下面的输入：
6. **分隔线**
你可以在一行中用三个以上的星号、减号、底线来建立一个分隔线，行内不能有其他东西。你也可以在星号或是减号中间插入空格。下面每种写法都可以建立分隔线：

7. **链接**
方块括号后面紧接着圆括号并插入网址链接即可，<>() 例如：

8. **字体**
+ 加粗: 要加粗的文字左右分别用两个 ** 号包起来
+ 斜体: 要倾斜的文字左右分别用一个 * 号包起来
+ 斜体加粗: 要倾斜和加粗的文字左右分别用三个*** 号包起来
+ 删除线: 要加删除线的文字左右分别用两个~~ 号包起来
+ 下划线: 可以通过HTML < u> < /u> 的标签来实现

9. **行内标记**
行内标记用 反引号 把它包起来' '，例如 this is python code
	
10. **插入图片**
![图片alt](图片地址 ''图片title'') ![图片alt](图片地址 ''图片title'')
接着一个方括号，里面放上图片的代替文字

11. **反斜杠**
Markdown可以利用反斜杠来插入一些在语法中有其它意义的符号，例如：如果你想要用星号加在文字旁边的方式来做出强调效果，你可以在星号的前面加上反斜杠：
12. **自动邮箱链接**
Markdown支持以比较简短的自动链接形式来处理电子邮件信箱，例如：
给我发邮件，欢迎骚扰h_xuetao@163.com
13. **注释**
可以通过三种方法实现：
+ 第一是通过 html 的 < !--  --> 标记；
+ 第二可以通过样式隐藏段落内容，即 < div style=display:none>；
+ 第三是通过 Markdown 自身的解析原理实现。

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4OTg3OTUzNjJdfQ==
-->