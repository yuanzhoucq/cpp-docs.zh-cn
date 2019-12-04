---
title: 编译器错误 C3195
ms.date: 11/04/2016
f1_keywords:
- C3195
helpviewer_keywords:
- C3195
ms.assetid: 97e4f681-812b-49e8-ba57-24b7817e3cd8
ms.openlocfilehash: c8274e121e953c3e51a0f2ff8c68c315759ce3e1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760421"
---
# <a name="compiler-error-c3195"></a>编译器错误 C3195

“operator”: 被保留并且不能用作 ref 类或值类型的成员。 必须使用“operator”关键字定义 CLR 或 WinRT 运算符

编译器检测到了使用 C++ 托管扩展语法的运算符定义。 必须使用运算符的C++语法。

下面的示例生成 C3195，并演示如何修复此错误：

```cpp
// C3195.cpp
// compile with: /clr /LD
#using <mscorlib.dll>
value struct V {
   static V op_Addition(V v, int i);   // C3195
   static V operator +(V v, char c);   // OK for new C++ syntax
};
```
