---
title: 错误 C1509
ms.date: 11/04/2016
f1_keywords:
- C1509
helpviewer_keywords:
- C1509
ms.assetid: 40dd100d-c6ba-451c-bd26-2c99ec1c36d6
ms.openlocfilehash: efd5b9dd5cdd7ee174bc786c38d9dd841e2ad6ce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397479"
---
# <a name="fatal-error-c1509"></a>错误 C1509

编译器限制： 函数 function 中的有太多异常处理程序状态。 简化函数

代码超过异常处理程序状态 （32,768 状态） 的内部限制。

最常见原因是此函数包含用户定义的类变量和算术运算符的复杂表达式。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复

1. 通过将公共子表达式分配给临时变量简化表达式。

1. 将函数拆分为较小的函数。