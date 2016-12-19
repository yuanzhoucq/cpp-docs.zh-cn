---
title: "编译器错误 C2107 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2107"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2107"
ms.assetid: 2866a121-884e-4bb5-8613-36de5817000e
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2107
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

非法索引，不允许间接寻址  
  
 下标应用于不是计算为指针的表达式。  
  
## 示例  
 如果错误地使用值类型的 `this` 指针来访问该类型的默认索引器，则会发生 C2107 错误。  有关详细信息，请参阅 [此指针的语义](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Semantics_of_the_this_pointer)。  
  
 下面的示例生成 C2107。  
  
```  
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