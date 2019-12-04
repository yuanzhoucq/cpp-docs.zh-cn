---
title: 编译器错误 C3642
ms.date: 11/04/2016
f1_keywords:
- C3642
helpviewer_keywords:
- C3642
ms.assetid: 429790c2-9614-4d85-b31c-687c8d8f83ff
ms.openlocfilehash: 7c3f9f05bf04c9a1c20fff7910836e7b50468a8e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742452"
---
# <a name="compiler-error-c3642"></a>编译器错误 C3642

"return_type/args"：无法从本机代码调用具有 __clrcall 调用约定的函数

不能从本机（非托管）代码中调用标记为[__clrcall](../../cpp/clrcall.md)调用约定的函数。

*return_type/args*是要尝试调用的函数的名称或 `__clrcall` 函数的类型。  当你通过函数指针调用时，会使用类型。

若要从本机上下文调用托管函数，可以添加一个 "包装" 函数，该函数将调用 `__clrcall` 函数。 或者，可以使用 CLR 封送机制;有关详细信息，请参阅[如何：使用 PInvoke 封送函数指针](../../dotnet/how-to-marshal-function-pointers-using-pinvoke.md)。

下面的示例生成 C3642：

```cpp
// C3642.cpp
// compile with: /clr
using namespace System;
struct S {
   void Test(String ^ s) {   // CLR type in signature, implicitly __clrcall
      Console::WriteLine(s);
   }
   void Test2(char * s) {
      Test(gcnew String(s));
   }
};

#pragma unmanaged
int main() {
   S s;
   s.Test("abc");   // C3642
   s.Test2("abc");   // OK
}
```
