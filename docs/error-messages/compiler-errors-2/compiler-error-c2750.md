---
title: 编译器错误 C2750
ms.date: 11/04/2016
f1_keywords:
- C2750
helpviewer_keywords:
- C2750
ms.assetid: 30450034-feb5-448c-9655-b8c5f3639695
ms.openlocfilehash: 943220fae035da8d6fc861d2abae435051381e1c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50453737"
---
# <a name="compiler-error-c2750"></a>编译器错误 C2750

type： 不能使用引用类型; 上的 new请改用 gcnew

若要创建的 CLR 类型，它将导致要放置在垃圾回收堆上的实例，实例必须使用[gcnew](../../windows/ref-new-gcnew-cpp-component-extensions.md)。

下面的示例生成 C2750:

```
// C2750.cpp
// compile with: /clr
ref struct Y1 {};

int main() {
   Y1 ^ x = new Y1;   // C2750

   // try the following line instead
   Y1 ^ x2 = gcnew Y1;
}
```