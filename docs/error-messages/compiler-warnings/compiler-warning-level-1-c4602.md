---
title: 编译器警告（等级 1）C4602
ms.date: 11/04/2016
f1_keywords:
- C4602
helpviewer_keywords:
- C4602
ms.assetid: c1f0300f-e2a2-4c9e-a7c3-4c7318d10509
ms.openlocfilehash: 7cacadea560dc5a68d396ac607deb3a5a3c236ee
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965904"
---
# <a name="compiler-warning-level-1-c4602"></a>编译器警告（等级 1）C4602

\#pragma pop_macro： "宏名" 否此标识符前面的 #pragma push_macro

如果你对于特定的宏使用 [pop_macro](../../preprocessor/pop-macro.md) ，你首先必须将宏的名称传递到 [push_macro](../../preprocessor/push-macro.md)。 例如，以下示例生成 C4602：

```cpp
// C4602.cpp
// compile with: /W1
int main()
{
   #pragma pop_macro("x")   // C4602 x is not on the stack
}
```