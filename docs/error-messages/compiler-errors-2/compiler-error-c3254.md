---
title: 编译器错误 C3254
ms.date: 11/04/2016
f1_keywords:
- C3254
helpviewer_keywords:
- C3254
ms.assetid: 93427b10-fa72-4e43-80d1-1a6e122f9f40
ms.openlocfilehash: 7e051c6c44d3b85f6f3faaf5380ecf54cba5d73c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173485"
---
# <a name="compiler-error-c3254"></a>编译器错误 C3254

显式重写： 类包含显式重写 override，但不是包含函数声明的接口派生

当您[显式重写](../../cpp/explicit-overrides-cpp.md)方法，包含该重写的类必须派生，直接或间接地，从包含该函数的类型将重写。

下面的示例生成 C3254:

```
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