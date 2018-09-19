---
title: 编译器错误 C3642 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3642
dev_langs:
- C++
helpviewer_keywords:
- C3642
ms.assetid: 429790c2-9614-4d85-b31c-687c8d8f83ff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: febd6f1a9a3b4bac8bbee59cbf8c5bead93c3fb3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047715"
---
# <a name="compiler-error-c3642"></a>编译器错误 C3642

return_type/参数： 不能包含 __clrcall 调用约定的本机代码中调用的函数

将标有一个函数[__clrcall](../../cpp/clrcall.md)调用约定不能从本机 （非托管） 代码调用。

*return_type/args*是函数的名称或类型的`__clrcall`想要调用的函数。  通过函数指针进行调用时，使用的类型。

若要从本机上下文调用托管的函数，您可以添加一个"包装器"函数，将调用`__clrcall`函数。 或者，可以使用 CLR 封送处理机制;请参阅[如何： 封送函数指针使用 PInvoke](../../dotnet/how-to-marshal-function-pointers-using-pinvoke.md)有关详细信息。

下面的示例生成 C3642:

```
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