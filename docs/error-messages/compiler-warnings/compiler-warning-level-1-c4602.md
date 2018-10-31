---
title: 编译器警告（等级 1）C4602
ms.date: 11/04/2016
f1_keywords:
- C4602
helpviewer_keywords:
- C4602
ms.assetid: c1f0300f-e2a2-4c9e-a7c3-4c7318d10509
ms.openlocfilehash: c719ae23ed3799debf2db9c8f2d82b3c49db3156
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50430383"
---
# <a name="compiler-warning-level-1-c4602"></a>编译器警告（等级 1）C4602

\#pragma pop_macro: macro name 前面没有 #pragma push_macro 此标识符

如果你对于特定的宏使用 [pop_macro](../../preprocessor/pop-macro.md) ，你首先必须将宏的名称传递到 [push_macro](../../preprocessor/push-macro.md)。 例如，以下示例生成 C4602：

```
// C4602.cpp
// compile with: /W1
int main()
{
   #pragma pop_macro("x")   // C4602 x is not on the stack
}
```