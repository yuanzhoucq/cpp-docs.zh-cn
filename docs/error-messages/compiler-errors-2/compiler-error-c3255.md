---
title: 编译器错误 C3255
ms.date: 11/04/2016
f1_keywords:
- C3255
helpviewer_keywords:
- C3255
ms.assetid: 877ffca2-fd92-44b6-9060-6091b928b1c1
ms.openlocfilehash: 43538ce87e1d832fcfc4fca882a9f129b917aad5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754207"
---
# <a name="compiler-error-c3255"></a>编译器错误 C3255

"值类型"：在本机堆上无法动态分配此值类型对象

包含托管成员的值类型的实例（请参阅[类和结构](../../extensions/classes-and-structs-cpp-component-extensions.md)）可以在堆栈上创建，但不能在堆上创建。

下面的示例生成 C3255：

```cpp
// C3255.cpp
// compile with: /clr
using namespace System;
value struct V {
   Object^ o;
};

value struct V2 {
   int i;
};

int main() {
   V* pv = new V;   // C3255
   V2* pv2 = new V2;
   V v2;
}
```
