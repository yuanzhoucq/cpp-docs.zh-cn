---
title: 表达式计算器错误 CXX0030
ms.date: 11/04/2016
f1_keywords:
- CXX0030
helpviewer_keywords:
- CAN0030
- CXX0030
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
ms.openlocfilehash: 1e52b238905fba5c310a89377b81548a1c6b5784
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500342"
---
# <a name="expression-evaluator-error-cxx0030"></a>表达式计算器错误 CXX0030

不可计算的表达式

顾名思义，调试器的表达式计算器无法获取表达式的值。 一个可能的原因是该表达式引用外部程序的地址空间的内存 （取消引用 null 指针是一个例子）。 Windows 不允许访问的外部程序的地址空间的内存。

您可能想要重写表达式，使用括号来控制计算顺序。

此错误是与 CAN0030 相同。