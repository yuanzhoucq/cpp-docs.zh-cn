---
title: 编译器错误 C3182
ms.date: 11/04/2016
f1_keywords:
- C3182
helpviewer_keywords:
- C3182
ms.assetid: f3681266-308e-4990-a979-8eef8920e186
ms.openlocfilehash: c6b183eb30dd0e617e69ab9aac58bea5cb721591
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761655"
---
# <a name="compiler-error-c3182"></a>编译器错误 C3182

"class"：托管或 WinRTtype 中的成员 using 声明或访问声明非法

[使用](../../cpp/using-declaration.md)声明在托管类的所有形式内无效。

下例生成了 C3182，并演示了如何对其进行修复。

```cpp
// C3182a.cpp
// compile with: /clr /c
ref struct B {
   void mf(int) {
   }
};

ref struct D : B {
   using B::mf;   // C3182, delete to resolve
   void mf(char) {
   }
};
```
