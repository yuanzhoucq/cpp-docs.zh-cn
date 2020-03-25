---
title: 错误 C1509
ms.date: 11/04/2016
f1_keywords:
- C1509
helpviewer_keywords:
- C1509
ms.assetid: 40dd100d-c6ba-451c-bd26-2c99ec1c36d6
ms.openlocfilehash: 0d1d7255dd64239a6a76bb15a1f309b43eac0d4b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202951"
---
# <a name="fatal-error-c1509"></a>错误 C1509

编译器限制：函数 "function" 中有太多异常处理程序状态。 化简函数

代码超出了异常处理程序状态的内部限制（32768）。

最常见的原因是该函数包含用户定义的类变量和算术运算符的复杂表达式。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复

1. 通过将常见子表达式分配给临时变量，简化表达式。

1. 将函数拆分为较小的函数。
