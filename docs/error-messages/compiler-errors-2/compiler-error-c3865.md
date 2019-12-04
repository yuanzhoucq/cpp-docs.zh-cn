---
title: 编译器错误 C3865
ms.date: 11/04/2016
f1_keywords:
- C3865
helpviewer_keywords:
- C3865
ms.assetid: 9bc62bb0-4fb8-4856-a5cf-c7cb4029a596
ms.openlocfilehash: 960c795fe934433e4e3cf79e4c01c49d00205b9b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761486"
---
# <a name="compiler-error-c3865"></a>编译器错误 C3865

"calling_convention"：只能用在本机成员函数上

调用约定用于作为全局函数或托管成员函数的函数。 调用约定只能用于本机（非托管）成员函数。

有关详细信息，请参阅[调用约定](../../cpp/calling-conventions.md)。

下面的示例生成 C3865：

```cpp
// C3865.cpp
// compile with: /clr
// processor: x86
void __thiscall Func(){}   // C3865

// OK
struct MyType {
   void __thiscall Func(){}
};
```
