---
title: 编译器错误 C2585
ms.date: 11/04/2016
f1_keywords:
- C2585
helpviewer_keywords:
- C2585
ms.assetid: 05bb1a9c-28fb-4a88-a1b5-aea85ebdee1c
ms.openlocfilehash: 57a0cd7a200c5bbb875821eb9e10314d98e58185
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177386"
---
# <a name="compiler-error-c2585"></a>编译器错误 C2585

到 "type" 的显式转换不明确

类型转换可能会产生多个结果。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 基于多个继承从类或结构类型转换。 如果该类型多次继承相同的基类，则转换函数或运算符必须使用范围解析（`::`）来指定要在转换中使用的继承类。

1. 已定义转换运算符和构造函数进行相同的转换。
