---
title: "编译器错误 C3642 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3642"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3642"
ms.assetid: 429790c2-9614-4d85-b31c-687c8d8f83ff
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# 编译器错误 C3642
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“return\_type\/args”: 不能从本机代码中使用 \_\_clrcall 调用约定调用函数  
  
 不能从本机（非托管）代码中调用使用 [\_\_clrcall](../../cpp/clrcall.md) 调用约定标记的函数。  
  
 *return\_type\/args* 是正尝试调用的函数的名称，或者是正尝试调用的 `__clrcall`函数的类型。通过函数指针进行调用时使用了类型。  
  
 若要从本机上下文调用托管函数，则可以添加一个将调用 `__clrcall` 函数的“包装”函数。  也可以使用 CLR 封送处理机制；有关更多信息，请参见[如何：使用 PInvoke 封送函数指针](../../dotnet/how-to-marshal-function-pointers-using-pinvoke.md)。  
  
 下面的示例生成 C3642：  
  
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