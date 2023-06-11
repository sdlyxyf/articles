Python 教程 — Python 3.12.0b1 文档

[![Logo](../_static/py.svg)](https://www.python.org/)

Theme Auto Light Dark

#### 上一个主题

[更新日志](../whatsnew/changelog.html "上一章")

#### 下一个主题

[1\. 课前甜点](appetite.html "下一章")

### 当前页面

-   [提交 Bug](../bugs.html)
-   [显示源码](https://github.com/python/cpython/blob/main/Doc/tutorial/index.rst)

### 导航

-   [索引](../genindex.html "总目录")
-   [模块](../py-modindex.html "Python 模块索引") |
-   [下一页](appetite.html "1. 课前甜点") |
-   [上一页](../whatsnew/changelog.html "更新日志") |
-   ![python logo](../_static/py.svg)
-   [Python](https://www.python.org/) »

-   [3.12.0b1 Documentation](../index.html) »
-   Python 教程
-   |
-   Theme Auto Light Dark |

# Python 教程[¶](#the-python-tutorial "永久链接至标题")

Python 是一门易于学习、功能强大的编程语言。它提供了高效的高级数据结构，还能简单有效地面向对象编程。Python 优雅的语法和动态类型以及解释型语言的本质，使它成为多数平台上写脚本和快速开发应用的理想语言。

Python 官网（[https://www.python.org/](https://www.python.org/)）上免费提供了 Python 解释器和扩展的标准库，包括源码和适用于各操作系统的机器码形式，并可自由地分发。Python 官网还包含许多免费的第三方 Python 模块、程序和工具发布包及文档链接。

Python 解释器易于扩展，使用 C 或 C++（或其他 C 能调用的语言）即可为 Python 扩展新功能和数据类型。Python 也可用作定制软件中的扩展程序语言。

本教程只是简单介绍了 Python 语言概念和功能。读者在阅读本教程时最好使用 Python 解释器以便随时动手练习。本教程中的所有示例都是相互独立的并可离线阅读。

标准库与模块的内容详见 [Python 标准库](../library/index.html#library-index)。[Python 语言参考手册](../reference/index.html#reference-index) 是更正规的语言定义。如要编写 C 或 C++ 扩展请参考 [扩展和嵌入 Python 解释器](../extending/index.html#extending-index) 和 [Python/C API 参考手册](../c-api/index.html#c-api-index)。此外，深入讲解 Python 的书籍也有很多。

本教程对每一个功能的介绍并不完整，甚至没有涉及全部常用功能，只是介绍了 Python 中最值得学习的功能，旨在让读者快速感受一下 Python 的特色。学完本教程的读者可以阅读和编写 Python 模块和程序，也可以继续学习 [Python 标准库](../library/index.html#library-index)。

强烈推荐阅读 [术语对照表](../glossary.html#glossary)。

-   [1\. 课前甜点](appetite.html)
-   [2\. Python 解释器](interpreter.html)
    -   [2.1. 调用解释器](interpreter.html#invoking-the-interpreter)
        -   [2.1.1. 传入参数](interpreter.html#argument-passing)
        -   [2.1.2. 交互模式](interpreter.html#interactive-mode)
    -   [2.2. 解释器的运行环境](interpreter.html#the-interpreter-and-its-environment)
        -   [2.2.1. 源文件的字符编码](interpreter.html#source-code-encoding)
-   [3\. Python 速览](introduction.html)
    -   [3.1. Python 用作计算器](introduction.html#using-python-as-a-calculator)
        -   [3.1.1. 数字](introduction.html#numbers)
        -   [3.1.2. 字符串](introduction.html#strings)
        -   [3.1.3. 列表](introduction.html#lists)
    -   [3.2. 走向编程的第一步](introduction.html#first-steps-towards-programming)
-   [4\. 其他流程控制工具](controlflow.html)
    -   [4.1. `if` 语句](controlflow.html#if-statements)
    -   [4.2. `for` 语句](controlflow.html#for-statements)
    -   [4.3. `range()` 函数](controlflow.html#the-range-function)
    -   [4.4. 循环中的 `break`、`continue` 语句及 `else` 子句](controlflow.html#break-and-continue-statements-and-else-clauses-on-loops)
    -   [4.5. `pass` 语句](controlflow.html#pass-statements)
    -   [4.6. `match` 语句](controlflow.html#match-statements)
    -   [4.7. 定义函数](controlflow.html#defining-functions)
    -   [4.8. 函数定义详解](controlflow.html#more-on-defining-functions)
        -   [4.8.1. 默认值参数](controlflow.html#default-argument-values)
        -   [4.8.2. 关键字参数](controlflow.html#keyword-arguments)
        -   [4.8.3. 特殊参数](controlflow.html#special-parameters)
            -   [4.8.3.1. 位置或关键字参数](controlflow.html#positional-or-keyword-arguments)
            -   [4.8.3.2. 仅位置参数](controlflow.html#positional-only-parameters)
            -   [4.8.3.3. 仅限关键字参数](controlflow.html#keyword-only-arguments)
            -   [4.8.3.4. 函数示例](controlflow.html#function-examples)
            -   [4.8.3.5. 小结](controlflow.html#recap)
        -   [4.8.4. 任意实参列表](controlflow.html#arbitrary-argument-lists)
        -   [4.8.5. 解包实参列表](controlflow.html#unpacking-argument-lists)
        -   [4.8.6. Lambda 表达式](controlflow.html#lambda-expressions)
        -   [4.8.7. 文档字符串](controlflow.html#documentation-strings)
        -   [4.8.8. 函数注解](controlflow.html#function-annotations)
    -   [4.9. 小插曲：编码风格](controlflow.html#intermezzo-coding-style)
-   [5\. 数据结构](datastructures.html)
    -   [5.1. 列表详解](datastructures.html#more-on-lists)
        -   [5.1.1. 用列表实现堆栈](datastructures.html#using-lists-as-stacks)
        -   [5.1.2. 用列表实现队列](datastructures.html#using-lists-as-queues)
        -   [5.1.3. 列表推导式](datastructures.html#list-comprehensions)
        -   [5.1.4. 嵌套的列表推导式](datastructures.html#nested-list-comprehensions)
    -   [5.2. `del` 语句](datastructures.html#the-del-statement)
    -   [5.3. 元组和序列](datastructures.html#tuples-and-sequences)
    -   [5.4. 集合](datastructures.html#sets)
    -   [5.5. 字典](datastructures.html#dictionaries)
    -   [5.6. 循环的技巧](datastructures.html#looping-techniques)
    -   [5.7. 深入条件控制](datastructures.html#more-on-conditions)
    -   [5.8. 序列和其他类型的比较](datastructures.html#comparing-sequences-and-other-types)
-   [6\. 模块](modules.html)
    -   [6.1. 模块详解](modules.html#more-on-modules)
        -   [6.1.1. 以脚本方式执行模块](modules.html#executing-modules-as-scripts)
        -   [6.1.2. 模块搜索路径](modules.html#the-module-search-path)
        -   [6.1.3. “已编译的” Python 文件](modules.html#compiled-python-files)
    -   [6.2. 标准模块](modules.html#standard-modules)
    -   [6.3. `dir()` 函数](modules.html#the-dir-function)
    -   [6.4. 包](modules.html#packages)
        -   [6.4.1. 从包中导入 \*](modules.html#importing-from-a-package)
        -   [6.4.2. 子包参考](modules.html#intra-package-references)
        -   [6.4.3. 多目录中的包](modules.html#packages-in-multiple-directories)
-   [7\. 输入与输出](inputoutput.html)
    -   [7.1. 更复杂的输出格式](inputoutput.html#fancier-output-formatting)
        -   [7.1.1. 格式化字符串字面值](inputoutput.html#formatted-string-literals)
        -   [7.1.2. 字符串 format() 方法](inputoutput.html#the-string-format-method)
        -   [7.1.3. 手动格式化字符串](inputoutput.html#manual-string-formatting)
        -   [7.1.4. 旧式字符串格式化方法](inputoutput.html#old-string-formatting)
    -   [7.2. 读写文件](inputoutput.html#reading-and-writing-files)
        -   [7.2.1. 文件对象的方法](inputoutput.html#methods-of-file-objects)
        -   [7.2.2. 使用 `json` 保存结构化数据](inputoutput.html#saving-structured-data-with-json)
-   [8\. 错误和异常](errors.html)
    -   [8.1. 句法错误](errors.html#syntax-errors)
    -   [8.2. 异常](errors.html#exceptions)
    -   [8.3. 异常的处理](errors.html#handling-exceptions)
    -   [8.4. 触发异常](errors.html#raising-exceptions)
    -   [8.5. 异常链](errors.html#exception-chaining)
    -   [8.6. 用户自定义异常](errors.html#user-defined-exceptions)
    -   [8.7. 定义清理操作](errors.html#defining-clean-up-actions)
    -   [8.8. 预定义的清理操作](errors.html#predefined-clean-up-actions)
    -   [8.9. Raising and Handling Multiple Unrelated Exceptions](errors.html#raising-and-handling-multiple-unrelated-exceptions)
    -   [8.10. Enriching Exceptions with Notes](errors.html#enriching-exceptions-with-notes)
-   [9\. 类](classes.html)
    -   [9.1. 名称和对象](classes.html#a-word-about-names-and-objects)
    -   [9.2. Python 作用域和命名空间](classes.html#python-scopes-and-namespaces)
        -   [9.2.1. 作用域和命名空间示例](classes.html#scopes-and-namespaces-example)
    -   [9.3. 初探类](classes.html#a-first-look-at-classes)
        -   [9.3.1. 类定义语法](classes.html#class-definition-syntax)
        -   [9.3.2. Class 对象](classes.html#class-objects)
        -   [9.3.3. 实例对象](classes.html#instance-objects)
        -   [9.3.4. 方法对象](classes.html#method-objects)
        -   [9.3.5. 类和实例变量](classes.html#class-and-instance-variables)
    -   [9.4. 补充说明](classes.html#random-remarks)
    -   [9.5. 继承](classes.html#inheritance)
        -   [9.5.1. 多重继承](classes.html#multiple-inheritance)
    -   [9.6. 私有变量](classes.html#private-variables)
    -   [9.7. 杂项说明](classes.html#odds-and-ends)
    -   [9.8. 迭代器](classes.html#iterators)
    -   [9.9. 生成器](classes.html#generators)
    -   [9.10. 生成器表达式](classes.html#generator-expressions)
-   [10\. 标准库简介](stdlib.html)
    -   [10.1. 操作系统接口](stdlib.html#operating-system-interface)
    -   [10.2. 文件通配符](stdlib.html#file-wildcards)
    -   [10.3. 命令行参数](stdlib.html#command-line-arguments)
    -   [10.4. 错误输出重定向和程序终止](stdlib.html#error-output-redirection-and-program-termination)
    -   [10.5. 字符串模式匹配](stdlib.html#string-pattern-matching)
    -   [10.6. 数学](stdlib.html#mathematics)
    -   [10.7. 互联网访问](stdlib.html#internet-access)
    -   [10.8. 日期和时间](stdlib.html#dates-and-times)
    -   [10.9. 数据压缩](stdlib.html#data-compression)
    -   [10.10. 性能测量](stdlib.html#performance-measurement)
    -   [10.11. 质量控制](stdlib.html#quality-control)
    -   [10.12. 自带电池](stdlib.html#batteries-included)
-   [11\. 标准库简介 —— 第二部分](stdlib2.html)
    -   [11.1. 格式化输出](stdlib2.html#output-formatting)
    -   [11.2. 模板](stdlib2.html#templating)
    -   [11.3. 使用二进制数据记录格式](stdlib2.html#working-with-binary-data-record-layouts)
    -   [11.4. 多线程](stdlib2.html#multi-threading)
    -   [11.5. 日志记录](stdlib2.html#logging)
    -   [11.6. 弱引用](stdlib2.html#weak-references)
    -   [11.7. 用于操作列表的工具](stdlib2.html#tools-for-working-with-lists)
    -   [11.8. 十进制浮点运算](stdlib2.html#decimal-floating-point-arithmetic)
-   [12\. 虚拟环境和包](venv.html)
    -   [12.1. 概述](venv.html#introduction)
    -   [12.2. 创建虚拟环境](venv.html#creating-virtual-environments)
    -   [12.3. 使用pip管理包](venv.html#managing-packages-with-pip)
-   [13\. 接下来？](whatnow.html)
-   [14\. 交互式编辑和编辑历史](interactive.html)
    -   [14.1. Tab 补全和编辑历史](interactive.html#tab-completion-and-history-editing)
    -   [14.2. 默认交互式解释器的替代品](interactive.html#alternatives-to-the-interactive-interpreter)
-   [15\. 浮点算术：争议和限制](floatingpoint.html)
    -   [15.1. 表示性错误](floatingpoint.html#representation-error)
-   [16\. 附录](appendix.html)
    -   [16.1. 交互模式](appendix.html#interactive-mode)
        -   [16.1.1. 错误处理](appendix.html#error-handling)
        -   [16.1.2. 可执行的Python脚本](appendix.html#executable-python-scripts)
        -   [16.1.3. 交互式启动文件](appendix.html#the-interactive-startup-file)
        -   [16.1.4. 定制模块](appendix.html#the-customization-modules)

#### 上一个主题

[更新日志](../whatsnew/changelog.html "上一章")

#### 下一个主题

[1\. 课前甜点](appetite.html "下一章")

### 当前页面

-   [提交 Bug](../bugs.html)
-   [显示源码](https://github.com/python/cpython/blob/main/Doc/tutorial/index.rst)

### 导航

-   [索引](../genindex.html "总目录")
-   [模块](../py-modindex.html "Python 模块索引") |
-   [下一页](appetite.html "1. 课前甜点") |
-   [上一页](../whatsnew/changelog.html "更新日志") |
-   ![python logo](../_static/py.svg)
-   [Python](https://www.python.org/) »

-   [3.12.0b1 Documentation](../index.html) »
-   Python 教程
-   |
-   Theme Auto Light Dark |

© [版权所有](../copyright.html) 2001-2023, Python Software Foundation.  
This page is licensed under the Python Software Foundation License Version 2.  
Examples, recipes, and other code in the documentation are additionally licensed under the Zero Clause BSD License.  
See [History and License](/license.html) for more information.  
  
The Python Software Foundation is a non-profit corporation. [Please donate.](https://www.python.org/psf/donations/)  
  
最后更新于 6月 05, 2023. [Found a bug](/bugs.html)?  
由 [Sphinx](https://www.sphinx-doc.org/) 4.5.0创建。
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQ2MTI3NzY5Ml19
-->