---
title: 编译器错误 C2217 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2217
dev_langs:
- C++
helpviewer_keywords:
- C2217
ms.assetid: 1ce1e3f5-4171-4376-804d-967f7e612935
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a4eb8b9fcaffa30f3a5ced5362a0f9d54a45f07e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050614"
---
# <a name="compiler-error-c2217"></a>编译器错误 C2217

attribute1 需要 attribute2

第一个函数属性需要第二个属性。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 中断 (`__interrupt`) 函数声明为`near`。 中断函数必须是`far`。

1. 中断用声明的函数`__stdcall`，或`__fastcall`。 中断函数必须使用 C 调用约定。

## <a name="example"></a>示例

如果您尝试将委托绑定到采用数目可变的参数的 CLR 函数，也可能发生 C2217。 如果该函数也具有 e param 数组重载，请改为使用的。 下面的示例生成 C2217。

```
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