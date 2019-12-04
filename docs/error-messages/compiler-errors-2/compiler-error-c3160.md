---
title: 编译器错误 C3160
ms.date: 11/04/2016
f1_keywords:
- C3160
helpviewer_keywords:
- C3160
ms.assetid: a250c433-8adf-43b9-8dee-c3794e09b0a5
ms.openlocfilehash: 4d6f415c8b3c8275ac45ef4d4313021100d9a833
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755143"
---
# <a name="compiler-error-c3160"></a>编译器错误 C3160

“pointer”: 托管或 WinRT 类的数据成员不能具有此类型

内部垃圾回收指针可能会指向托管或 WinRT 类的内部。 因为它们比整个对象的指针慢，并且需要垃圾回收器进行特殊处理，因此你不能将内部托管的指针声明为类的成员。

以下示例生成 C3160：

```cpp
// C3160.cpp
// compile with: /clr
ref struct A {
   // cannot create interior pointers inside a class
   interior_ptr<int> pg;   // C3160
   int g;   // OK
   int* pg2;   // OK
};

int main() {
   interior_ptr<int> pg2;   // OK
}
```
