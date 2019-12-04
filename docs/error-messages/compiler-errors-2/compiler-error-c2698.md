---
title: 编译器错误 C2698
ms.date: 11/04/2016
f1_keywords:
- C2698
helpviewer_keywords:
- C2698
ms.assetid: 3ebfe395-c20b-4c56-9980-ca9ed8653382
ms.openlocfilehash: 6129ff691f804b31fdb8cb487ac4609e4bca6ef2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755182"
---
# <a name="compiler-error-c2698"></a>编译器错误 C2698

"声明 1" 的 using 声明不能与 "声明 2" 的现有 using 声明共存

为数据成员[使用了声明](../../cpp/using-declaration.md)后，不允许使用同一范围内的任何 using 声明，因为只能重载函数。

下面的示例生成 C2698：

```cpp
// C2698.cpp
struct A {
   int x;
};

struct B {
   int x;
};

struct C : A, B {
   using A::x;
   using B::x;   // C2698
}
```
