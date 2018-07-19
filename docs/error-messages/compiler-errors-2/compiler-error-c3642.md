---
title: 编译器错误 C3642 |Microsoft 文档
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
ms.openlocfilehash: c9e841bcc4fbcb62d6a2d1e6f51f47a73bd2e06a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33264512"
---
# <a name="compiler-error-c3642"></a>编译器错误 C3642
return_type/参数： 无法从本机代码调用约定的 __clrcall 与调用函数  
  
 将标有一个函数[__clrcall](../../cpp/clrcall.md)调用约定不能从本机 （非托管） 代码调用。  
  
 *return_type/args*是函数的名称或的一种`__clrcall`尝试调用的函数。  通过函数指针进行调用时，使用的类型。  
  
 若要从本地上下文调用托管的函数，你可以添加将调用"包装器"函数`__clrcall`函数。 或者，你可以使用 CLR 封送处理机制;请参阅[How to： 封送函数指针使用 PInvoke](../../dotnet/how-to-marshal-function-pointers-using-pinvoke.md)有关详细信息。  
  
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