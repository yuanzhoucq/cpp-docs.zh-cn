---
title: 编译器错误 C2750
ms.date: 11/04/2016
f1_keywords:
- C2750
helpviewer_keywords:
- C2750
ms.assetid: 30450034-feb5-448c-9655-b8c5f3639695
ms.openlocfilehash: 34d19e8e9f51c90c48ec0d429f98bb82e3d829d4
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58778905"
---
# <a name="compiler-error-c2750"></a>编译器错误 C2750

type： 不能使用引用类型; 上的 new请改用 gcnew

若要创建的 CLR 类型，它将导致要放置在垃圾回收堆上的实例，实例必须使用[gcnew](../../extensions/ref-new-gcnew-cpp-component-extensions.md)。

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