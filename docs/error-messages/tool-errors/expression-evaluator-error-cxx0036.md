---
title: 表达式计算器错误 CXX0036
ms.date: 11/04/2016
f1_keywords:
- CXX0036
helpviewer_keywords:
- CXX0036
- CAN0036
ms.assetid: 383404be-df5b-4eec-b113-df21bb5d269d
ms.openlocfilehash: 164fd9ee00071e218e5bb4f3ab00febc618725a7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195495"
---
# <a name="expression-evaluator-error-cxx0036"></a>表达式计算器错误 CXX0036

错误的上下文 {...} specification

使用上下文运算符（ **{}** ）时，有几个错误可能会生成此消息。

- 未正确赋予上下文运算符（ **{}** ）的语法。

   上下文运算符的语法为：

     {*function*，*module*，*dll*}*表达式*

   这将指定*表达式*的上下文。 上下文运算符与类型转换的优先级和用法相同。

   可以省略尾随逗号。 如果任何*函数*、*模块*或*dll*包含文字逗号，则必须将整个名称括在括号中。

- 函数名拼写错误，或在指定的模块或动态链接库中不存在。

   因为 C 是一种区分大小写的语言，所以必须在与源中定义的完全相同的情况下提供*函数*。

- 未能找到该模块或 DLL。

   检查指定模块或 DLL 的完整路径名称。

此错误与 CAN0036 相同。
