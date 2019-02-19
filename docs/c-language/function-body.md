---
title: 函数体
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C], syntax
- variables, function syntax
- function definitions, function body
- function body
ms.assetid: f7e74822-fac8-4dc8-8f3a-2b1611da4640
ms.openlocfilehash: c227640e45943fb57b1029a4f03329241d1d6b34
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/12/2019
ms.locfileid: "56146861"
---
# <a name="function-body"></a>函数体

函数体是包含指定函数行为的语句的复合语句。

## <a name="syntax"></a>语法

function-definition：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*<sub>opt</sub> *attribute-seq*<sub>opt</sub> *declarator* *declaration-list*<sub>opt</sub> *compound-statement*

/\* *attribute-seq* 为 Microsoft 专用 \*/

compound-statement：/\* 函数体 \*/<br/>
nchen&nbsp;&nbsp;&nbsp;&nbsp;**{** *declaration-list*<sub>opt</sub> *statement-list*<sub>opt</sub> **}**

在函数体中声明的变量（称为“局部变量”）具有 auto 存储类，除非另行指定。 调用函数时，将为局部变量创建存储并执行本地初始化。 执行控制权将传递给 compound-statement 中的第一个语句并继续传递，直到执行了 return 语句或到达函数体的末尾。 控制权随后返回到调用功能的点。

如果该函数返回了值，则必须执行包含表达式的 return 语句。 如果没有执行 return 语句或 return 语句不包含表达式，则函数的返回值是不确定的。

## <a name="see-also"></a>请参阅

[C 函数定义](../c-language/c-function-definitions.md)
