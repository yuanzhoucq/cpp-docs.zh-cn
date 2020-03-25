---
title: 编译器警告（等级 3）C4243
ms.date: 11/04/2016
f1_keywords:
- C4243
helpviewer_keywords:
- C4243
ms.assetid: ca72f9ad-ce0b-43a9-a68c-106e1f8b90ef
ms.openlocfilehash: 5900202a88eb7dc0575c5e97a58b20b0ef290a49
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161550"
---
# <a name="compiler-warning-level-3-c4243"></a>编译器警告（等级 3）C4243

"转换类型" 转换已从 "type1" 转换为 "type2"，但不可访问

指向派生类的指针转换为指向基类的指针，但派生类继承具有私有或受保护访问权限的基类。

下面的示例生成 C4243：

```cpp
// C4243.cpp
// compile with: /W3
// C4243 expected
struct B {
   int f() {
      return 0;
   };
};

struct D : private B {};
struct E : public B {};

int main() {
   // Delete the following 2 lines to resolve.
   int (D::* d)() = (int(D::*)()) &B::f;
   d;

   int (E::* e)() = (int(E::*)()) &B::f; // OK
   e;
}
```
