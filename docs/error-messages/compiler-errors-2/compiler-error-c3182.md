---
title: 编译器错误 C3182
ms.date: 11/04/2016
f1_keywords:
- C3182
helpviewer_keywords:
- C3182
ms.assetid: f3681266-308e-4990-a979-8eef8920e186
ms.openlocfilehash: 6866c7bbcee0a4097e490b344c79a6eec7f94570
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626741"
---
# <a name="compiler-error-c3182"></a>编译器错误 C3182

class： 成员 using 声明或访问声明是非法的托管或 WinRTtype 中

一个[使用](../../cpp/using-declaration.md)声明托管类的所有窗体中无效。

下例生成了 C3182，并演示了如何对其进行修复。

```
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
