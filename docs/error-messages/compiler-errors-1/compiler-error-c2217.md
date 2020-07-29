---
title: 编译器错误 C2217
ms.date: 11/04/2016
f1_keywords:
- C2217
helpviewer_keywords:
- C2217
ms.assetid: 1ce1e3f5-4171-4376-804d-967f7e612935
ms.openlocfilehash: b033d95b127a45451a776cdc336ea7d2649d3716
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87209742"
---
# <a name="compiler-error-c2217"></a>编译器错误 C2217

"attribute1" 需要 "attribute2"

第一个函数属性需要第二个属性。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 将中断（ `__interrupt` ）函数声明为 `near` 。 中断函数必须是 `far` 。

1. 中断函数用 **`__stdcall`** 、或声明 **`__fastcall`** 。 中断函数必须使用 C 调用约定。

## <a name="example"></a>示例

如果尝试将委托绑定到采用可变数量的参数的 CLR 函数，也会发生 C2217。 如果函数也具有 e 参数数组重载，请改用。 下面的示例生成 C2217。

```cpp
// C2217.cpp
// compile with: /clr
using namespace System;
delegate void MyDel(String^, Object^, Object^, ...);   // C2217
delegate void MyDel2(String ^, array<Object ^> ^);   // OK

int main() {
   MyDel2^ wl = gcnew MyDel2(Console::WriteLine);
   array<Object ^ > ^ x = gcnew array<Object ^>(2);
   x[0] = safe_cast<Object^>(0);
   x[1] = safe_cast<Object^>(1);

   // wl("{0}, {1}", 0, 1);
   wl("{0}, {1}", x);
}
```
