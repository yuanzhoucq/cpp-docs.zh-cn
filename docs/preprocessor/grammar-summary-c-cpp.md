---
title: 预处理器语法摘要 (C/C++)
description: 定义并描述 Microsoft C/C++编译器（MSVC）预处理器语法语法。
ms.date: 08/29/2019
helpviewer_keywords:
- grammar
- preprocessor, grammar
ms.assetid: 0acb6e9b-364c-4ef8-ace4-7be980521121
ms.openlocfilehash: 99e7e8218a80e28d67767392cadfb5c4918a3bfe
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302180"
---
# <a name="preprocessor-grammar-summary-cc"></a>预处理器语法摘要 (C/C++)

本文介绍 C 和C++预处理器的正式语法。 其中包含预处理指令和运算符的语法。 有关详细信息，请参阅[预处理器](../preprocessor/preprocessor.md)和[杂注指令以及 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)。

## <a name="definitions"></a>语法摘要的定义

终止符是语法定义中的终结点。 不提供其他解决方法。 终止符包括保留字和用户定义的标识符的集。

非终止符是语法中的占位符。 它们中的大多数是在此语法摘要中的其他位置定义的。 定义可是递归的。 以下非终止符在 *C++语言参考*的 "[词法约定](../cpp/lexical-conventions.md)" 部分中定义：

*常量*、*常量表达式*、*标识符*、*关键字*、*运算符*、*标点符号*

可选组件由带下标的 <sub>opt</sub> 指示。 例如，下面的语法指示括在大括号中的可选表达式：

**{** *expression*<sub>opt</sub> **}**

## <a name="conventions"></a>文档约定

约定将对不同的语法组件使用不同的字体特性。 符号和字体如下所示：

| 特性 | 描述 |
|---------------|-----------------|
| nonterminal | 斜体类型指示非终止符。 |
| **#include** | 粗体类型的终止符是必须按所示方式输入的文本保留字和符号。 此上下文中的字符始终区分大小写。 |
| <sub>opt</sub> | 后跟 <sub>opt </sub> 的非终止符始终是可选的。|
| default typeface | 用此字样描述或列出的集中的字符可在语句中用作终止符。 |

跟在非终止符之后的冒号 (:) 引入其定义。 替代定义在单独的行上列出。

在代码语法块中，默认字样中的这些符号具有特殊含义：

| 符号 | 描述 |
|---|---|
| \[ ] | 方括号括起一个可选元素。 |
| {\|} | 大括号环绕替代元素，用竖线分隔。 |
| ... | 指示上一个元素模式可以重复。 |

在代码语法块中，逗号（`,`）、句点（`.`）、分号（`;`）、冒号（`:`）、括号（`( )`）、双引号（`"`）和单引号（`'`）都是文本。

## <a name="grammar"></a>预处理器语法

*控件行*： \
&nbsp;&nbsp;&nbsp;&nbsp; **#define** *标识符* *标记-字符串*<sub>opt</sub>\
&nbsp;&nbsp;&nbsp;&nbsp; **#define** *标识符* **（** *标识符*<sub>opt</sub> **，** ... **，** *标识符*<sub>opt</sub> **）** *标记字符串*<sub>opt</sub>\
&nbsp; **#include** &nbsp;&nbsp; **&nbsp;\**
&nbsp;&nbsp;&nbsp;&nbsp; **#include** **\<>** _\_
&nbsp;&nbsp;&nbsp;&nbsp; **#line** *数字序列* **"** _filename_ **"** <sub>opt</sub>\
&nbsp;&nbsp;&nbsp;&nbsp; **#undef** *标识符*\
&nbsp;&nbsp;&nbsp;&nbsp; **#error** *标记-字符串*\
&nbsp;&nbsp;&nbsp;&nbsp; **#pragma** *token-string*

*常量-表达式*： \
&nbsp;定义的 &nbsp;&nbsp;&nbsp; **（** *标识符* **）** \
&nbsp;&nbsp;&nbsp;&nbsp;**定义** *标识符*\
&nbsp;任何其他常量表达式的 &nbsp;&nbsp;&nbsp;

*条件*： \
&nbsp;&nbsp;&nbsp;&nbsp;*如果-部分* *elif*<sub>opt</sub>*else-部分*<sub>opt</sub>*endif 行*

*如果-部分*： \
&nbsp;&nbsp;&nbsp;&nbsp;*的行* *文本*

*如果为-line*： \
&nbsp;&nbsp;&nbsp;&nbsp; **#if** *常量表达式*\
&nbsp;&nbsp;&nbsp;&nbsp; **#ifdef** *标识符*\
&nbsp;&nbsp;&nbsp;&nbsp; **#ifndef** *标识符*

*elif*：
&nbsp;&nbsp;&nbsp;&nbsp;*elif* *文本*\
&nbsp;&nbsp;&nbsp;&nbsp;*elif* *elif* *文本*

*elif*： \
&nbsp;&nbsp;&nbsp;&nbsp; **#elif** *constant-expression*

*else-部分*： \
&nbsp;&nbsp;&nbsp;&nbsp;*行* *文本*

*else-line*： \
&nbsp;&nbsp;&nbsp;&nbsp; **#else**

*endif 行*： \
&nbsp;&nbsp;&nbsp;&nbsp; **#endif**

*数字序列*： \
&nbsp;&nbsp;&nbsp;&nbsp;*数字*\
&nbsp;&nbsp;&nbsp;&nbsp;*数字序列* *数字*

*数字*: 1\
&nbsp;&nbsp;&nbsp;&nbsp;0 1 2 3 4 5 6 7 8 9

*标记-字符串*： \
&nbsp;&nbsp;&nbsp;&nbsp;的标记字符串

*令牌*： \
&nbsp;&nbsp;&nbsp;&nbsp;*关键字*\
&nbsp;*标识符*&nbsp;&nbsp;&nbsp;\
&nbsp;&nbsp;&nbsp;&nbsp;*常量*\
&nbsp;&nbsp;&nbsp;&nbsp;*运算符*\
&nbsp;&nbsp;&nbsp;&nbsp;*punctuator*

*filename*： \
&nbsp;&nbsp;&nbsp;合法操作系统文件名 &nbsp;

*路径-规范*： \
&nbsp;&nbsp;&nbsp;&nbsp;合法文件路径

*文本*： \
&nbsp;任意文本序列 &nbsp;&nbsp;&nbsp;

> [!NOTE]
> 以下非终止符在 *C++语言参考*：*常量*、*常量表达式*、*标识符*、*关键字*、*运算符*和*标点符号*的 "[词法约定](../cpp/lexical-conventions.md)" 部分中展开。


## <a name="see-also"></a>请参阅

[C/C++预处理器参考](../preprocessor/c-cpp-preprocessor-reference.md)
