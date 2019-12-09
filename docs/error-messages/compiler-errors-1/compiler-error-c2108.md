---
title: 编译器错误 C2108
ms.date: 11/04/2016
f1_keywords:
- C2108
helpviewer_keywords:
- C2108
ms.assetid: c84f0b47-5e2c-47d2-8edb-427a40e17c36
ms.openlocfilehash: 069f369627f42314cc14688a9e0c0a55808db507
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752023"
---
# <a name="compiler-error-c2108"></a>编译器错误 C2108

下标不是整型

数组下标是一个非整数表达式。

## <a name="example"></a>示例

如果错误地使用值类型的 `this` 指针访问类型的默认索引器，则可能会发生 C2108。 有关详细信息，请参阅[this 指针的语义](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Semantics_of_the_this_pointer)。

下面的示例生成 C2108。

```cpp
// C2108.cpp
// compile with: /clr
using namespace System;

value struct B {
   property Double default[Double] {
      Double get(Double data) {
         return data*data;
      }
   }
   void Test() {
      Console::WriteLine("{0}", this[3.3]);   // C2108
      Console::WriteLine("{0}", this->default[3.3]);   // OK
   }
};

int main() {
   B ^ myb = gcnew B();
   myb->Test();
}
```
