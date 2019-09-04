---
title: 预处理器语法
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor
- grammar, preprocessor
- preprocessor, grammar
ms.assetid: 6cd33fad-0b08-4592-9be8-7359c43e24e9
ms.openlocfilehash: f0916e3cc9bbdb398db693286dacc4517df03557
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222256"
---
# <a name="preprocessor-grammar"></a>预处理器语法

*控件行*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#define***标识符* *标记-字符串*<sub>opt</sub>\
&nbsp;&nbsp;&nbsp;&nbsp; **#define***标识符* **(** &#x2800;标识符&#x200B;<sub>opt</sub> **,** ... **,** *标识符*&#x200B; <sub></sub>opt&#x2800; **)** *令牌-字符串*<sub>opt</sub>\
&nbsp;&nbsp;&nbsp;&nbsp; **#include** **"** _路径规范_ **"** \
&nbsp;&nbsp;&nbsp;&nbsp; **#include** **\<** _路径规范_ **>** \
&nbsp;&nbsp;&nbsp;&nbsp; **#line***数字序列* **"** _filename_ **"** &#x200B; <sub>opt</sub>  \
&nbsp;&nbsp;&nbsp;&nbsp; **#undef***标识符*\
&nbsp;&nbsp;&nbsp;&nbsp; **#error***标记-字符串*\
&nbsp;&nbsp;&nbsp;&nbsp; **#pragma** *token-string*

*常量-表达式*: \
&nbsp;&nbsp;&nbsp;&nbsp;**定义 (** &#x2800;*标识符*&#x2800; **)** \
&nbsp;&nbsp;&nbsp;&nbsp;**定义***标识符*\
&nbsp;&nbsp;&nbsp;&nbsp;任何其他常数表达式

*条件*: \
&nbsp;&nbsp;&nbsp;&nbsp;*如果-部分* *elif*<sub>opt</sub>*else-部分*<sub>opt</sub>*endif 行*

*如果-部分*: \
&nbsp;&nbsp;&nbsp;&nbsp;*如果为-line* *文本*

*如果为-line*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#if***常量表达式*\
&nbsp;&nbsp;&nbsp;&nbsp; **#ifdef***标识符*\
&nbsp;&nbsp;&nbsp;&nbsp; **#ifndef***标识符*

*elif*:
&nbsp;&nbsp;&nbsp;&nbsp;*elif* *文本*\
&nbsp;&nbsp;&nbsp;&nbsp;*elif* *elif* *文本*

*elif*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#elif** *constant-expression*

*else-部分*: \
&nbsp;&nbsp;&nbsp;&nbsp;*else-线条* *文本*

*else-line*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#else**

*endif 行*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#endif**

*数字序列*: \
&nbsp;&nbsp;&nbsp;&nbsp;*年份*\
&nbsp;&nbsp;&nbsp;&nbsp;digit-sequence digit

*数字*: 1
&nbsp;&nbsp;&nbsp;&nbsp;0 1 2 3 4 5 6 7 8 9

*标记-字符串*: \
&nbsp;&nbsp;&nbsp;&nbsp;标记字符串

*令牌*: \
&nbsp;&nbsp;&nbsp;&nbsp;*关键字*\
&nbsp;&nbsp;&nbsp;&nbsp;*标志*\
&nbsp;&nbsp;&nbsp;&nbsp;*常量*\
&nbsp;&nbsp;&nbsp;&nbsp;*操作员*\
&nbsp;&nbsp;&nbsp;&nbsp;*punctuator*

*filename*: \
&nbsp;&nbsp;&nbsp;&nbsp;合法操作系统文件名

*路径-规范*: \
&nbsp;&nbsp;&nbsp;&nbsp;合法文件路径

*文本*: \
&nbsp;&nbsp;&nbsp;&nbsp;任何文本序列

> [!NOTE]
> 以下非终止符在 *C++语言参考*的 "[词法约定](../cpp/lexical-conventions.md)" 部分中展开:*常量*、*常量表达式*、*标识符*、*关键字*、*运算符*和*标点符号*。

## <a name="see-also"></a>请参阅

[语法摘要 (C/C++)](../preprocessor/grammar-summary-c-cpp.md)
