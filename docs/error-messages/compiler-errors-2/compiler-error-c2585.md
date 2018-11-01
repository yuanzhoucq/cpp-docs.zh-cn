---
title: 编译器错误 C2585
ms.date: 11/04/2016
f1_keywords:
- C2585
helpviewer_keywords:
- C2585
ms.assetid: 05bb1a9c-28fb-4a88-a1b5-aea85ebdee1c
ms.openlocfilehash: 812ab15aacd1f6a215c6a5beb7781983859fe858
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593253"
---
# <a name="compiler-error-c2585"></a>编译器错误 C2585

显式转换成 type 不明确

类型转换可以生成多个结果。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 从基于多个继承的类或结构类型转换。 如果该类型不止一次继承相同的基类，转换函数或运算符必须使用范围解析 (`::`) 以指定的要在转换中使用的继承类。

1. 转换运算符和构造函数定义了进行相同的转换。