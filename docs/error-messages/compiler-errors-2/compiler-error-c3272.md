---
title: 编译器错误 C3272
ms.date: 11/04/2016
f1_keywords:
- C3272
helpviewer_keywords:
- C3272
ms.assetid: 7cdf254d-f207-4116-a1bf-7386f3b82a6f
ms.openlocfilehash: 3e4348dcce0cfd04234b515877d788e5330f8e4c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62365684"
---
# <a name="compiler-error-c3272"></a>编译器错误 C3272

“symbol”：符号需要 FieldOffset，因为它是用 StructLayout(LayoutKind::Explicit) 定义的 typename 类型的成员

当 `StructLayout(LayoutKind::Explicit)` 有效时，必须用 `FieldOffset`来标记字段。

下面的示例生成 C3272：

```
// C3272_2.cpp
// compile with: /clr /c
using namespace System;
using namespace System::Runtime::InteropServices;

[StructLayout(LayoutKind::Explicit)]
ref struct X
{
   int data_;   // C3272
   // try the following line instead
   // [FieldOffset(0)] int data_;
};
```
