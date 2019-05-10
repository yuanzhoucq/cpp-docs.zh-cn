---
title: 编译器错误 C2698
ms.date: 11/04/2016
f1_keywords:
- C2698
helpviewer_keywords:
- C2698
ms.assetid: 3ebfe395-c20b-4c56-9980-ca9ed8653382
ms.openlocfilehash: f643b7d8c035b4d1d7d8806feb5b121cf76d7796
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367572"
---
# <a name="compiler-error-c2698"></a>编译器错误 C2698

using 声明为 declaration 1 不能与现有 using 声明共存声明 2

一旦您有[using 声明](../../cpp/using-declaration.md)数据成员，任何使用不允许使用相同的名称与同一范围中声明，因为只有函数才可以进行重载。

下面的示例生成 C2698:

```
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