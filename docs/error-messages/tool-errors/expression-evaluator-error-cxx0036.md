---
title: 表达式计算器错误 CXX0036 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0036
dev_langs:
- C++
helpviewer_keywords:
- CXX0036
- CAN0036
ms.assetid: 383404be-df5b-4eec-b113-df21bb5d269d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e2d82a1254a11dbda3164ea1c350dc14e2b1a122
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050107"
---
# <a name="expression-evaluator-error-cxx0036"></a>表达式计算器错误 CXX0036

错误上下文 {...} specification

可以通过使用上下文运算符中的多个错误的任何生成此消息 (**{}**)。

- 上下文运算符的语法 (**{}**) 提供了不正确。

     上下文运算符的语法是：

     {*函数*，*模块*，*dll*}*表达式*

     这将指定的上下文*表达式*。 上下文运算符类型强制转换为具有相同的优先级和使用情况。

     可以忽略尾随逗号。 如果任一*函数*，*模块*，或*dll*包含文本的逗号，则必须将整个名称括在括号中。

- 函数名称存在拼写错误，或指定的模块或动态链接库中不存在。

     C 是区分大小写的语言，因为*函数*必须在源中定义的正确大小写中提供。

- 找不到模块或 DLL。

     检查指定的模块或 DLL 的完整路径名称。

此错误是与 CAN0036 相同。