---
title: 表达式计算器错误 CXX0030 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0030
dev_langs:
- C++
helpviewer_keywords:
- CAN0030
- CXX0030
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb2921013d116b7d8f02e1e29380ca3cd14086b9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102801"
---
# <a name="expression-evaluator-error-cxx0030"></a>表达式计算器错误 CXX0030

不可计算的表达式

顾名思义，调试器的表达式计算器无法获取表达式的值。 一个可能的原因是该表达式引用外部程序的地址空间的内存 （取消引用 null 指针是一个例子）。 Windows 不允许访问的外部程序的地址空间的内存。

您可能想要重写表达式，使用括号来控制计算顺序。

此错误是与 CAN0030 相同。