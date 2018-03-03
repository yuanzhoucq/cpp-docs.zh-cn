---
title: "编译器错误 C3642 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3642
dev_langs:
- C++
helpviewer_keywords:
- C3642
ms.assetid: 429790c2-9614-4d85-b31c-687c8d8f83ff
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3dace0204f4534ee630924bd443d028efc2afc14
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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