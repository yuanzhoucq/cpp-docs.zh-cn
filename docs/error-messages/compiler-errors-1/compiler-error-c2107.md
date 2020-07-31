---
title: 编译器错误 C2107
ms.date: 11/04/2016
f1_keywords:
- C2107
helpviewer_keywords:
- C2107
ms.assetid: 2866a121-884e-4bb5-8613-36de5817000e
ms.openlocfilehash: 1be2ebb82aca481df9efbbc4ccdd54466ae60a3f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214784"
---
# <a name="compiler-error-c2107"></a>编译器错误 C2107

非法索引，不允许间接寻址

下标应用于不计算为指针的表达式。

## <a name="example"></a>示例

如果错误地使用 **`this`** 值类型的指针访问类型的默认索引器，则可能会发生 C2107。 有关详细信息，请参阅[this 指针的语义](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Semantics_of_the_this_pointer)。

下面的示例生成 C2107。

```cpp
// C2107.cpp
// compile with: /clr
using namespace System;

value struct B {
   property String ^ default[String ^] {
      String ^ get(String ^ data) {
         return "abc";
      }
   }
   void Test() {
      Console::WriteLine("{0}", this["aa"]);   // C2107
      Console::WriteLine("{0}", this->default["aa"]);   // OK
   }
};

int main() {
   B ^ myb = gcnew B();
   myb->Test();
}
```
