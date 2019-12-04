---
title: 编译器错误 C3254
ms.date: 11/04/2016
f1_keywords:
- C3254
helpviewer_keywords:
- C3254
ms.assetid: 93427b10-fa72-4e43-80d1-1a6e122f9f40
ms.openlocfilehash: 6b9ff41fb4f45d9570869ca90e3c6091cc03a58a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754246"
---
# <a name="compiler-error-c3254"></a>编译器错误 C3254

"explicit override"：类包含显式重写 "override"，但不从包含函数声明的接口派生

[显式重写](../../cpp/explicit-overrides-cpp.md)方法时，包含重写的类必须直接或间接从包含要重写的函数的类型派生。

下面的示例生成 C3254：

```cpp
// C3254.cpp
__interface I
{
   void f();
};

__interface I1 : I
{
};

struct A /* : I1 */
{
   void I1::f()
   {   // C3254, uncomment : I1 to resolve this C3254
   }
};

int main()
{
}
```
